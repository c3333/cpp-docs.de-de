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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: 227f9e31c689b0259c429e2ffd9fce074903bd71
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/07/2020
ms.locfileid: "82920178"
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

*FD*<br/>
Dateideskriptor der geöffneten Datei.

*mode*<br/>
Der Typ des Dateizugriffs.

## <a name="return-value"></a>Rückgabewert

Jede dieser Funktionen gibt einen Zeiger auf den geöffneten Stream zurück. Ein NULL-Zeigerwert gibt einen Fehler an. Wenn ein Fehler auftritt, wird der ungültige Parameterhandler aufgerufen, so wie dies unter [Parametervalidierung](../../c-runtime-library/parameter-validation.md) beschrieben wird. Wenn die weitere Ausführung zugelassen wird, wird **errno** entweder auf **EBADF**festgelegt, was auf einen fehlerhaften Dateideskriptor hinweist, oder auf **EINVAL**, das angibt, dass der *Modus* ein NULL-Zeiger war.

Weitere Informationen zu diesen und anderen Fehlercodes finden Sie unter [_doserrno, errno, _sys_errlist und _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Hinweise

Die **_fdopen** -Funktion ordnet einen e/a-Datenstrom mit der von *FD*identifizierten Datei zu und ermöglicht so, dass eine Datei, die für e/a auf niedriger Ebene geöffnet ist, gepuffert und formatiert wird. **_wfdopen** ist eine breit Zeichen Version von **_fdopen**. Das *Mode* -Argument für **_wfdopen** ist eine Zeichenfolge mit breit Zeichen. **_wfdopen** und **_fdopen** andernfalls identisch.

Dateideskriptoren, die an **_fdopen** übermittelt werden, befinden sich im Besitz der zurückgegebenen **Datei #b0** Streams. Wenn **_fdopen** erfolgreich ist, sollten Sie nicht [ \_close](close.md) für den Dateideskriptor aufzurufen. Der Aufruf von [fclose](fclose-fcloseall.md) in der zurückgegebenen **Datei #b0** auch den Dateideskriptor schließt.

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen hierzu finden Sie unter [globaler Status in der CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Zuordnung generischer Textroutinen

|Tchar.h-Routine|\_Unicode und \_MBCS sind nicht definiert.|\_Definierte MBCS|\_Unicode definiert|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tfdopen**|**_fdopen**|**_fdopen**|**_wfdopen**|

Die Zeichenfolge im *Modus* gibt den Typ des Datei Zugriffs an, der für die Datei angefordert wird:

| *mode* | Zugriff |
|--------|--------|
| **r** | Öffnet zum Lesen. Wenn die Datei nicht vorhanden ist oder nicht gefunden werden kann, schlägt der **fopen** -Befehl fehl. |
| **Löw** | Öffnet eine leere Datei zum Schreiben. Wenn die angegebene Datei vorhanden ist, wird ihr Inhalt zerstört. |
| **ein** | Öffnet zum Schreiben am Ende der Datei (Anhängen). Erstellt die Datei, wenn sie nicht vorhanden ist. |
| **"r +"** | Öffnet sowohl zum Lesen als auch zum Schreiben. Die Datei muss vorhanden sein. |
| **"w +"** | Öffnet eine leere Datei zum Lesen und Schreiben. Wenn die Datei vorhanden ist, wird ihr Inhalt zerstört. |
| **"a +"** | Öffnet sich zum Lesen und Anfügen. Erstellt die Datei, wenn sie nicht vorhanden ist. |

Wenn eine Datei mit dem Zugriffstyp **"a"** oder **"a +"** geöffnet wird, erfolgen alle Schreibvorgänge am Ende der Datei. Der Dateizeiger kann mithilfe von [fseek](fseek-fseeki64.md) oder [Rewind](rewind.md)neu positioniert werden. er wird jedoch immer wieder zurück an das Ende der Datei verschoben, bevor ein Schreibvorgang durchgeführt wird. Folglich können vorhandene Daten nicht überschrieben werden. Wenn der Zugriffstyp **"r +"**, **"w +"** oder **"a +** " angegeben wird, sind sowohl Lese-als auch Schreibvorgänge zulässig (die Datei ist zum Aktualisieren geöffnet). Wenn Sie jedoch zwischen lesen und schreiben wechseln, muss ein dazwischenliegende [fflush](fflush.md)-, [fsetpos](fsetpos.md)-, [fseek](fseek-fseeki64.md)-oder [Rewind](rewind.md) -Vorgang vorhanden sein. Wenn Sie möchten, können Sie die aktuelle Position für den [fsetpos](fsetpos.md) -oder [fseek](fseek-fseeki64.md) -Vorgang angeben.

Zusätzlich zu den obigen Werten können die folgenden Zeichen auch im- *Modus* enthalten sein, um den Übersetzungsmodus für Zeilen Umleitungs Zeichen anzugeben:

| *mode* modusmodifizierer | Verhalten |
|-----------------|----------|
| **Bund** | Öffnen im Textmodus (übersetzt). Im Textmodus werden Wagenrücklauf-/Zeilenvorschub-Kombinationen (CR-LF) bei der Eingabe in einzelne Zeilenvorschübe (LF) übersetzt. LF-Zeichen werden bei der Ausgabe in CR-LF-Kombinationen übersetzt. Außerdem wird STRG+Z bei der Eingabe als EOF-Zeichen interpretiert. |
| **b** | Wird im binären (nicht übersetzten) Modus geöffnet. Alle Übersetzungen aus dem **t** -Modus werden unterdrückt. |
| **scher** | Aktivieren Sie das commitflag für den zugeordneten *Dateinamen* , damit der Inhalt des Datei Puffers direkt auf den Datenträger geschrieben wird, wenn entweder **fflush** oder **_flushall** aufgerufen wird. |
| **n** | Setzen Sie das commitflag für den zugeordneten *Dateinamen* auf "No-Commit" zurück. Dies ist die Standardeinstellung. Außerdem wird das globale commitflag überschrieben, wenn Sie das Programm mit COMMODE. obj verknüpfen. Der Standardwert des globalen commitflags lautet "No-Commit", es sei denn, Sie verknüpfen das Programm explizit mit COMMODE. obj. |

Die *Optionen "* **t**", " **c**" und " **n** " sind Microsoft-Erweiterungen für " **f Open** " und " **_fdopen** Verwenden Sie sie nicht, wenn Sie die ANSI-Portabilität beibehalten möchten.

Wenn " **t** " oder " **b** " im *Modus*nicht angegeben wird, wird der Standard Übersetzungsmodus durch die globale Variable [ \_"f Mode](../../c-runtime-library/fmode.md)" definiert. Wenn **t** oder **b** dem Argument vorangestellt wird, schlägt die Funktion fehl und gibt NULL zurück. Eine Erörterung von Text- und Binärmodi finden Sie unter [Text- und Binärmodusdatei-E/A](../../c-runtime-library/text-and-binary-mode-file-i-o.md).

Gültige Zeichen für die in **fopen** und **_fdopen** verwendete *modus*zeichenfolge entsprechen *Oflag* -Argumenten, die in [\_Open](open-wopen.md) und [\_sopen](sopen-wsopen.md)verwendet werden, wie in dieser Tabelle dargestellt:

|Zeichen in der *Mode* -Zeichenfolge|Entsprechender *Oflag* -Wert für **_open** und **_sopen**|
|---------------------------------|---------------------------------------------------|
|**ein**|**\_O\_wronly &#124; \_o\_Append** (in der Regel ** \_\_o wronly &#124; \_o\_- \_Anweisung\_&#124; o Append**)|
|**a +**|**\_O\_rdwr &#124; \_o\_Append** (i. d. ** \_r. o\_rdwr \_&#124;\_ \_o\_Append &#124; o | anfüat** )|
|**r**|**\_O\_rdonly**|
|**r +**|**\_O\_rdwr**|
|**w**|**\_O\_wronly** (in der Regel ** \_o\_ \_wronly\_&#124; o- \_&#124;\_o trunc**)|
|**w +**|**\_O\_rdwr** (in der Regel ** \_\_o rdwr &#124; \_o\_&#124; \_o\_trunc**)|
|**b**|**\_O\_-Binärdatei**|
|**Bund**|**\_O\_-Text**|
|**scher**|Keine|
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
[\_DUP, \_dup2](dup-dup2.md)<br/>
["f" \_, "vollständig"](fclose-fcloseall.md)<br/>
["Open" \_, "WF"](fopen-wfopen.md)<br/>
[freopen, \_wfreopen](freopen-wfreopen.md)<br/>
[\_Öffnen, \_Wopen](open-wopen.md)<br/>
