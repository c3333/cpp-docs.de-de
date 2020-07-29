---
title: _pipe
ms.date: 4/2/2020
api_name:
- _pipe
- _o__pipe
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
- pipe
- _pipe
helpviewer_keywords:
- pipes, creating
- _pipe function
- pipes
- pipe function
ms.assetid: 8d3e9800-4041-44b5-9e93-2df0b0354a75
ms.openlocfilehash: 692a891549e0c84d6297b108918d9d7c58495ef7
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87234041"
---
# <a name="_pipe"></a>_pipe

Erstellt eine Pipe zum Lesen und Schreiben.

> [!IMPORTANT]
> Diese API kann nicht in Anwendungen verwendet werden, die in Windows-Runtime ausgeführt werden. Weitere Informationen finden Sie im Artikel [CRT functions not supported in Universal Windows Platform apps (In Apps für die universelle Windows-Plattform nicht unterstützte CRT-Funktionen)](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntax

```C
int _pipe(
   int *pfds,
   unsigned int psize,
   int textmode
);
```

### <a name="parameters"></a>Parameter

*PFDs*<br/>
Zeiger auf ein Array von zwei **`int`** , das Lese-und Schreib Dateideskriptoren enthalten soll.

*Psize*<br/>
Menge des zugesicherten Arbeitsspeichers.

*TextMode*<br/>
Dateimodus.

## <a name="return-value"></a>Rückgabewert

Gibt bei Erfolg 0 zurück. Gibt-1 zurück, um einen Fehler anzugeben. Bei einem Fehler wird **errno** auf einen der folgenden Werte festgelegt:

- **EMFILE**: gibt an, dass keine weiteren Dateideskriptoren verfügbar sind.

- Die **Datei**, die einen Überlauf der Systemdatei Tabelle angibt.

- Ein **Format, das angibt, dass**entweder das Array- *PFDs* ein NULL-Zeiger ist oder dass ein ungültiger Wert für *TextMode* gegeben wurde.

Weitere Informationen zu diesen und anderen Rückgabecodes finden Sie unter [errno, _doserrno, _sys_errlist und _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Bemerkungen

Die **_pipe** -Funktion erstellt eine *Pipe*, bei der es sich um einen künstlichen e/a-Kanal handelt, den ein Programm verwendet, um Informationen an andere Programme zu übergeben. Eine Pipe ähnelt einer Datei, da sie über einen Dateizeiger, einen Dateideskriptor oder über beides verfügt. Es kann aus ihr gelesen oder in sie geschrieben werden, indem die Ein- und Ausgabefunktionen der Standardbibliothek verwendet werden. Eine Pipe repräsentiert jedoch weder eine bestimmte Datei noch ein bestimmtes Gerät. Stattdessen repräsentiert die Pipe einen temporären Speicher im Arbeitsspeicher, der vom Arbeitsspeicher des Programms unabhängig ist und vollständig über das Betriebssystem gesteuert wird.

**_pipe** ähnelt **_open** , öffnet jedoch die Pipe zum Lesen und schreiben und gibt zwei Dateideskriptoren anstelle eines zurück. Das Programm kann beide Seiten der Pipe verwenden oder diejenige Seite schließen, die sie nicht benötigt. Beispielsweise erstellt der Befehlsprozessor in Windows eine Pipe, wenn ein Befehl wie **Program1**  |  **Program2**ausgeführt wird.

Der Standardausgabe Deskriptor von **Program1** wird an den Schreib Deskriptor der Pipe angefügt. Der Standardeingabe Deskriptor von **Program2** wird an den lesedeskriptor der Pipe angefügt. Hierdurch entfällt die Notwendigkeit, temporäre Dateien zu erstellen, um Informationen an andere Programme zu übergeben.

Die **_pipe** -Funktion gibt zwei Dateideskriptoren an die Pipe im *PFDs* -Argument zurück. Das Element *PFDs*[0] enthält den Lese Deskriptor, und das Element *PFDs*[1] enthält den Schreib Deskriptor. Pipedateideskriptoren werden auf die gleiche Weise wie andere Dateideskriptoren verwendet. (Die Eingabe-und Ausgabefunktionen auf niedriger Ebene **_read** und **_write** können aus einer Pipe lesen und in eine Pipe schreiben.) Um das Ende der Pipe-Bedingung zu erkennen, suchen Sie nach einer **_read** -Anforderung, die 0 als Anzahl der gelesenen Bytes zurückgibt.

Das *Psize* -Argument gibt die Größe des Arbeitsspeichers in Bytes an, die für die Pipe reserviert werden soll. Das *TextMode* -Argument gibt den Übersetzungsmodus für die Pipe an. Die Manifest-Konstante **_O_TEXT** die eine Text Übersetzung angibt, und die Konstante **_O_BINARY** die binäre Übersetzung angibt. (Eine Beschreibung von Text-und binärmodi finden Sie [unter "f Open", _wfopen](fopen-wfopen.md) .) Wenn das *TextMode* -Argument 0 ist, verwendet **_pipe** den Standard Übersetzungsmodus, der von der Variablen Default-Mode [_fmode](../../c-runtime-library/fmode.md)angegeben wird.

In Multithreadprogrammen wird keine Sperre ausgeführt. Die zurückgegebenen Dateideskriptoren werden neu geöffnet und sollten von keinem Thread referenziert werden, bis der **_pipe** -Vorgang beendet ist.

Um die **_pipe** -Funktion für die Kommunikation zwischen einem übergeordneten Prozess und einem untergeordneten Prozess zu verwenden, muss für jeden Prozess nur ein Deskriptor in der Pipe geöffnet sein. Die Deskriptoren müssen entgegengesetzt sein: Wenn das übergeordnete Element über einen geöffneten Lesedeskriptor verfügt, muss das untergeordnete Element über einen geöffneten Schreibdeskriptor verfügen. Die einfachste Möglichkeit hierfür ist das bitweise OR ( **|** ) des **_O_NOINHERIT** -Flags mit *TextMode*. Verwenden Sie dann **_dup** oder **_dup2** , um eine vererbbare Kopie des pipedeskriptors zu erstellen, die Sie an das untergeordnete Element übergeben möchten. Schließen Sie den ursprünglichen Deskriptor, und starten Sie dann den untergeordneten Prozess. Schließen Sie nach dem Startaufruf den doppelten Deskriptor im übergeordneten Prozess. Weitere Informationen finden Sie im zweiten Beispiel weiter unten in diesem Artikel.

Im Windows-Betriebssystem wird eine Pipe zerstört, wenn alle zugehörigen Deskriptoren geschlossen sind. (Wenn alle Lese Deskriptoren auf der Pipe geschlossen wurden, verursacht das Schreiben in die Pipe einen Fehler.) Alle Lese-und Schreibvorgänge auf der Pipe warten, bis genügend Daten oder ausreichend Pufferspeicher zum Abschluss der e/a-Anforderung vorhanden sind.

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen hierzu finden Sie unter [globaler Status in der CRT](../global-state.md).

## <a name="requirements"></a>Anforderungen

|-Routine zurückgegebener Wert|Erforderlicher Header|Optionaler Header|
|-------------|---------------------|---------------------|
|**_pipe**|\<io.h>|\<fcntl.h>, 1 \<errno.h> 2|

1 für **_O_BINARY** -und **_O_TEXT** Definitionen.

2 **errno** -Definitionen.

Weitere Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Bibliotheken

Alle Versionen [C-Laufzeitbibliotheken](../../c-runtime-library/crt-library-features.md).

## <a name="example-1"></a>Beispiel 1

```C
// crt_pipe.c
/* This program uses the _pipe function to pass streams of
* text to spawned processes.
*/

#include <stdlib.h>
#include <stdio.h>
#include <io.h>
#include <fcntl.h>
#include <process.h>
#include <math.h>

enum PIPES { READ, WRITE }; /* Constants 0 and 1 for READ and WRITE */
#define NUMPROBLEM 8

int main( int argc, char *argv[] )
{

   int fdpipe[2];
   char hstr[20];
   int pid, problem, c;
   int termstat;

   /* If no arguments, this is the spawning process */
   if( argc == 1 )
   {

      setvbuf( stdout, NULL, _IONBF, 0 );

      /* Open a set of pipes */
      if( _pipe( fdpipe, 256, O_BINARY ) == -1 )
          exit( 1 );

      /* Convert pipe read descriptor to string and pass as argument
       * to spawned program. Program spawns itself (argv[0]).
       */
      _itoa_s( fdpipe[READ], hstr, sizeof(hstr), 10 );
      if( ( pid = _spawnl( P_NOWAIT, argv[0], argv[0],
            hstr, NULL ) ) == -1 )
          printf( "Spawn failed" );

      /* Put problem in write pipe. Since spawned program is
       * running simultaneously, first solutions may be done
       * before last problem is given.
       */
      for( problem = 1000; problem <= NUMPROBLEM * 1000; problem += 1000)
      {

         printf( "Son, what is the square root of %d?\n", problem );
         _write( fdpipe[WRITE], (char *)&problem, sizeof( int ) );

      }

      /* Wait until spawned program is done processing. */
      _cwait( &termstat, pid, WAIT_CHILD );
      if( termstat & 0x0 )
         printf( "Child failed\n" );

      _close( fdpipe[READ] );
      _close( fdpipe[WRITE] );

   }

   /* If there is an argument, this must be the spawned process. */
   else
   {

      /* Convert passed string descriptor to integer descriptor. */
      fdpipe[READ] = atoi( argv[1] );

      /* Read problem from pipe and calculate solution. */
      for( c = 0; c < NUMPROBLEM; c++ )
      {

        _read( fdpipe[READ], (char *)&problem, sizeof( int ) );
        printf( "Dad, the square root of %d is %3.2f.\n",
                 problem, sqrt( ( double )problem ) );

      }
   }
}
```

```Output
Son, what is the square root of 1000?
Son, what is the square root of 2000?
Son, what iDad, the square root of 1000 is 31.62.
Dad, the square root of 2000 is 44.72.
s the square root of 3000?
Dad, the square root of 3000 is 54.77.
Son, what is the square root of 4000?
Dad, the square root of 4000 is 63.25.
Son, what is the square root of 5000?
Dad, the square root of 5000 is 70.71.
Son, what is the square root of 6000?
SonDad, the square root of 6000 is 77.46.
, what is the square root of 7000?
Dad, the square root of 7000 is 83.67.
Son, what is the square root of 8000?
Dad, the square root of 8000 is 89.44.
```

## <a name="example-2"></a>Beispiel 2

Dies ist eine einfache Filteranwendung. Er erzeugt die Anwendung crt_pipe_beeper, nachdem eine Pipe erstellt wurde, die das erzeugte stdout-Objekt der Anwendung auf den Filter lenkt. Der Filter entfernt ASCII 7(Signalton)-Zeichen.

```C
// crt_pipe_beeper.c

#include <stdio.h>
#include <string.h>

int main()
{
   int   i;
   for(i=0;i<10;++i)
      {
         printf("This is speaker beep number %d...\n\7", i+1);
      }
   return 0;
}
```

Die tatsächliche Filteranwendung:

```C
// crt_pipe_BeepFilter.C
// arguments: crt_pipe_beeper.exe

#include <windows.h>
#include <process.h>
#include <memory.h>
#include <string.h>
#include <stdio.h>
#include <fcntl.h>
#include <io.h>

#define   OUT_BUFF_SIZE 512
#define   READ_FD 0
#define   WRITE_FD 1
#define   BEEP_CHAR 7

char szBuffer[OUT_BUFF_SIZE];

int Filter(char* szBuff, ULONG nSize, int nChar)
{
   char* szPos = szBuff + nSize -1;
   char* szEnd = szPos;
   int nRet = nSize;

   while (szPos > szBuff)
   {
      if (*szPos == nChar)
         {
            memmove(szPos, szPos+1, szEnd - szPos);
            --nRet;
         }
      --szPos;
   }
   return nRet;
}

int main(int argc, char** argv)
{
   int nExitCode = STILL_ACTIVE;
   if (argc >= 2)
   {
      HANDLE hProcess;
      int fdStdOut;
      int fdStdOutPipe[2];

      // Create the pipe
      if(_pipe(fdStdOutPipe, 512, O_NOINHERIT) == -1)
         return   1;

      // Duplicate stdout file descriptor (next line will close original)
      fdStdOut = _dup(_fileno(stdout));

      // Duplicate write end of pipe to stdout file descriptor
      if(_dup2(fdStdOutPipe[WRITE_FD], _fileno(stdout)) != 0)
         return   2;

      // Close original write end of pipe
      _close(fdStdOutPipe[WRITE_FD]);

      // Spawn process
      hProcess = (HANDLE)_spawnvp(P_NOWAIT, argv[1],
       (const char* const*)&argv[1]);

      // Duplicate copy of original stdout back into stdout
      if(_dup2(fdStdOut, _fileno(stdout)) != 0)
         return   3;

      // Close duplicate copy of original stdout
      _close(fdStdOut);

      if(hProcess)
      {
         int nOutRead;
         while   (nExitCode == STILL_ACTIVE)
         {
            nOutRead = _read(fdStdOutPipe[READ_FD],
             szBuffer, OUT_BUFF_SIZE);
            if(nOutRead)
            {
               nOutRead = Filter(szBuffer, nOutRead, BEEP_CHAR);
               fwrite(szBuffer, 1, nOutRead, stdout);
            }

            if(!GetExitCodeProcess(hProcess,(unsigned long*)&nExitCode))
               return 4;
         }
      }
   }
   return nExitCode;
}
```

```Output
This is speaker beep number 1...
This is speaker beep number 2...
This is speaker beep number 3...
This is speaker beep number 4...
This is speaker beep number 5...
This is speaker beep number 6...
This is speaker beep number 7...
This is speaker beep number 8...
This is speaker beep number 9...
This is speaker beep number 10...
```

## <a name="see-also"></a>Siehe auch

[Prozess-und Umgebungs Steuerung](../../c-runtime-library/process-and-environment-control.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
