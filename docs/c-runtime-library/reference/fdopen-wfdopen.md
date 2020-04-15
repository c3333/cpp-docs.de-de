---
title: _fdopen, _wfdopen
ms.date: 4/2/2020
api_name:
- _fdopen
- _wfdopen
- _o__fdopen
- _o__wfdopen
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
- api-ms-win-crt-math-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _tfdopen
- _fdopen
- _wfdopen
- wfdopen
- tfdopen
helpviewer_keywords:
- wfdopen function
- _fdopen function
- _wfdopen function
- tfdopen function
- fdopen function
- _tfdopen function
- streams, associating with files
ms.assetid: 262757ff-1e09-4472-a5b6-4325fc28f971
ms.openlocfilehash: 82a7e891e8bd6031ebbf761534b6df7cd8488d36
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81347386"
---
# <a name="_fdopen-_wfdopen"></a>_fdopen, _wfdopen

Verknüpft einen Stream mit einer Datei, die zuvor für E/A auf niedriger Ebene geöffnet war.

## <a name="syntax"></a>Syntax

```C
FILE *_fdopen(
   int fd,
   const char *mode
);
FILE *_wfdopen(
   int fd,
   const wchar_t *mode
);
```

### <a name="parameters"></a>Parameter

*Fd*<br/>
Dateideskriptor der geöffneten Datei.

*Modus*<br/>
Der Typ des Dateizugriffs.

## <a name="return-value"></a>Rückgabewert

Jede dieser Funktionen gibt einen Zeiger auf den geöffneten Stream zurück. Ein NULL-Zeigerwert gibt einen Fehler an. Wenn ein Fehler auftritt, wird der ungültige Parameterhandler aufgerufen, so wie dies unter [Parametervalidierung](../../c-runtime-library/parameter-validation.md) beschrieben wird. Wenn die Ausführung fortgesetzt werden darf, wird **errno** entweder auf **EBADF**, was auf einen fehlerhaften Dateideskriptor hinweist, oder **AUF EINVAL**festgelegt, was darauf hinweist, dass *der Modus* ein Nullzeiger war.

Weitere Informationen zu diesen und anderen Fehlercodes finden Sie unter [_doserrno, errno, _sys_errlist und _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Bemerkungen

Die **_fdopen-Funktion** ordnet der Datei, die durch *fd*identifiziert wird, einen E/A-Stream zu und ermöglicht so das Puffern und Formatieren einer Datei, die für E/A-Werte geöffnet wird. **_wfdopen** ist eine breit **gefächerte**Version von _fdopen ; Das *modus-Argument* für **_wfdopen** ist eine Zeichenfolge mit großen Zeichen. **_wfdopen** und **_fdopen** verhalten sich ansonsten identisch.

Dateideskriptoren, **die** an _fdopen übergeben werden, sind im Besitz des zurückgegebenen **FILE &#42;-Streams.** Wenn **_fdopen** erfolgreich ist, rufen Sie [ \_den Dateideskriptor](close.md) nicht auf. Wenn Sie [fclose](fclose-fcloseall.md) auf dem zurückgegebenen **FILE-&#42;** aufrufen, wird auch der Dateideskriptor geschlossen.

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen dazu finden Sie [unter Globaler Status in der CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Zuordnung generischer Textroutinen

|Tchar.h-Routine|\_UNICODE \_und MBCS nicht definiert|\_MBCS definiert|\_UNICODE definiert|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tfdopen**|**_fdopen**|**_fdopen**|**_wfdopen**|

Die *Moduszeichenfolge* gibt den Typ des für die Datei angeforderten Dateizugriffs an:

| *Modus* | Zugriff |
|--------|--------|
| **"r"** | Öffnet zum Lesen. Wenn die Datei nicht vorhanden ist oder nicht gefunden werden kann, schlägt der **Fopen-Aufruf** fehl. |
| **"w"** | Öffnet eine leere Datei zum Schreiben. Wenn die angegebene Datei vorhanden ist, wird ihr Inhalt zerstört. |
| **"a"** | Öffnet zum Schreiben am Ende der Datei (Anhängen). Erstellt die Datei, wenn sie nicht vorhanden ist. |
| **"r+"** | Öffnet sowohl zum Lesen als auch zum Schreiben. Die Datei muss vorhanden sein. |
| **"w+"** | Öffnet eine leere Datei zum Lesen und Schreiben. Wenn die Datei vorhanden ist, wird ihr Inhalt zerstört. |
| **"a+"** | Öffnet sich zum Lesen und Anfügen. Erstellt die Datei, wenn sie nicht vorhanden ist. |

Wenn eine Datei mit dem Zugriffstyp **"a"** oder **"a+"** geöffnet wird, werden alle Schreibvorgänge am Ende der Datei ausgeführt. Der Dateizeiger kann mithilfe von [fseek](fseek-fseeki64.md) oder [reswind](rewind.md)neu positioniert werden, aber er wird immer wieder an das Ende der Datei verschoben, bevor ein Schreibvorgang ausgeführt wird. Daher können vorhandene Daten nicht überschrieben werden. Wenn der Zugriffstyp **"r+"**, **"w+"** oder **"a+"** angegeben ist, sind sowohl Lesen als auch Schreiben zulässig (die Datei soll für "update" geöffnet sein). Wenn Sie jedoch zwischen Lesen und Schreiben wechseln, muss es einen dazwischenliegenden [fflush](fflush.md)-, [fsetpos](fsetpos.md), [fseek](fseek-fseeki64.md)oder [Respulvorgang](rewind.md) geben. Sie können die aktuelle Position für den [Fsetpos-](fsetpos.md) oder [fseek-Vorgang](fseek-fseeki64.md) angeben, wenn Sie möchten.

Zusätzlich zu den oben genannten Werten können die folgenden Zeichen auch in den *Modus* einbezogen werden, um den Übersetzungsmodus für Zeilenumleinenzeichen anzugeben:

| *mode* Modusmodifizierer | Verhalten |
|-----------------|----------|
| **T** | Öffnen im Textmodus (übersetzt). Im Textmodus werden Wagenrücklauf-/Zeilenvorschub-Kombinationen (CR-LF) bei der Eingabe in einzelne Zeilenvorschübe (LF) übersetzt. LF-Zeichen werden bei der Ausgabe in CR-LF-Kombinationen übersetzt. Außerdem wird STRG+Z bei der Eingabe als EOF-Zeichen interpretiert. |
| **B** | Wird im binären (nicht übersetzten) Modus geöffnet. Alle Übersetzungen aus dem **t-Modus** werden unterdrückt. |
| **C** | Aktivieren Sie das Commit-Flag für den zugeordneten *Dateinamen,* damit der Inhalt des Dateipuffers direkt auf den Datenträger geschrieben wird, wenn entweder **fflush** oder **_flushall** aufgerufen wird. |
| **n** | Setzen Sie das Commit-Flag für den zugeordneten *Dateinamen* auf "no-commit" zurück. Dies ist die Standardoption. Es überschreibt auch das globale Commit-Flag, wenn Sie Ihr Programm mit Commode.obj verknüpfen. Der Standardwert des globalen Commit-Flags ist "no-commit", es sei denn, Sie verknüpfen Ihr Programm explizit mit Commode.obj. |

Die Optionen **t**, **c**und **n** *sind* Microsoft-Erweiterungen für **fopen** und **_fdopen**. Verwenden Sie sie nicht, wenn Sie die ANSI-Portabilität beibehalten möchten.

Wenn **t** oder **b** im *Modus*nicht angegeben ist, wird der Standard-Übersetzungsmodus durch die globale Variable [ \_fmode](../../c-runtime-library/fmode.md)definiert. Wenn dem Argument **t** oder **b** ein Vorzeichen gesetzt wird, schlägt die Funktion fehl und gibt NULL zurück. Eine Erörterung von Text- und Binärmodi finden Sie unter [Text- und Binärmodusdatei-E/A](../../c-runtime-library/text-and-binary-mode-file-i-o.md).

Gültige Zeichen für die in **fopen** und **_fdopen** verwendete *modus*zeichenfolge entsprechen *Oflag* -Argumenten, die in [\_Open](open-wopen.md) und [\_sopen](sopen-wsopen.md)verwendet werden, wie in dieser Tabelle dargestellt:

|Zeichen in *der Moduszeichenfolge*|Äquivalent *des lag-Werts* für **_open** und **_sopen**|
|---------------------------------|---------------------------------------------------|
|**Eine**|**\_O\_WRONLY \_\_&#124; O APPEND** (normalerweise ** \_\_O WRONLY \_&#124; O\_CREAT \_&#124; O\_APPEND**)|
|**a+**|**\_O\_RDWR \_\_&#124; O APPEND** (normalerweise ** \_\_O RDWR \_&#124; O\_APPEND \_&#124; O\_CREAT** )|
|**R**|**\_O\_RDONLY**|
|**r+**|**\_O\_RDWR**|
|**w**|**\_O\_WRONLY** (in der Regel ** \_O\_WRONLY &#124; \_O\_CREAT &#124; \_O\_TRUNC**)|
|**w+**|**\_O\_RDWR** (in der Regel ** \_O\_RDWR &#124; \_O\_CREAT &#124; \_O\_TRUNC**)|
|**B**|**\_O\_BINARY**|
|**T**|**\_O\_TEXT**|
|**C**|Keine|
|**n**|Keine|

## <a name="requirements"></a>Anforderungen

|Funktion|Erforderlicher Header|
|--------------|---------------------|
|**_fdopen**|\<stdio.h>|
|**_wfdopen**|\<stdio.h> oder \<wchar.h>|

Weitere Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Beispiel

```c
// crt_fdopen.c
// This program opens a file by using low-level
// I/O, then uses _fdopen to switch to stream
// access. It counts the lines in the file.

#include <stdlib.h>
#include <stdio.h>
#include <fcntl.h>
#include <io.h>
#include <share.h>

int main( void )
{
   FILE *stream;
   int  fd, count = 0;
   char inbuf[128];

   // Open a file.
   if( _sopen_s( &fd, "crt_fdopen.txt", _O_RDONLY, _SH_DENYNO, 0 ) )
      exit( 1 );

   // Get stream from file descriptor.
   if( (stream = _fdopen( fd, "r" )) == NULL )
      exit( 1 );

   while( fgets( inbuf, 128, stream ) != NULL )
      count++;

   // After _fdopen, close by using fclose, not _close.
   fclose( stream );
   printf( "Lines in file: %d\n", count );
}
```

### <a name="input-crt_fdopentxt"></a>Eingabe: crt_fdopen.txt

```Input
Line one
Line two
```

### <a name="output"></a>Output

```Output
Lines in file: 2
```

## <a name="see-also"></a>Siehe auch

[Stream-E/A](../../c-runtime-library/stream-i-o.md)<br/>
[\_dup, \_dup2](dup-dup2.md)<br/>
[fclose, \_fcloseall](fclose-fcloseall.md)<br/>
[fopen, \_wfopen](fopen-wfopen.md)<br/>
[freopen, \_wfreopen](freopen-wfreopen.md)<br/>
[\_offen, \_wopen](open-wopen.md)<br/>
