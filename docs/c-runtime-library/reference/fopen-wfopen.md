---
title: fopen, _wfopen
ms.date: 4/2/2020
api_name:
- _wfopen
- fopen
- _o__wfopen
- _o_fopen
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
- fopen
- _wfopen
- _tfopen
- corecrt_wstdio/_wfopen
- stdio/fopen
helpviewer_keywords:
- opening files, for file I/O
- wfopen function
- tfopen function
- _tfopen function
- _wfopen function
- files [C++], opening
- fopen function
ms.assetid: e868993f-738c-4920-b5e4-d8f2f41f933d
ms.openlocfilehash: 4b9fa6542996b2c16128a841e2611b85e995be2a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81346407"
---
# <a name="fopen-_wfopen"></a>fopen, _wfopen

Öffnet eine Datei. Es sind sicherere Versionen dieser Funktionen verfügbar, die eine zusätzliche Parameterüberprüfung durchführen und Fehlercodes zurückgeben. Siehe dazu [fopen_s, _wfopen_s](fopen-s-wfopen-s.md).

## <a name="syntax"></a>Syntax

```C
FILE *fopen(
   const char *filename,
   const char *mode
);
FILE *_wfopen(
   const wchar_t *filename,
   const wchar_t *mode
);
```

### <a name="parameters"></a>Parameter

*Dateiname*<br/>
Dateiname

*Modus*<br/>
Art des Zugriffs, der aktiviert ist.

## <a name="return-value"></a>Rückgabewert

Jede dieser Funktionen gibt einen Zeiger auf die geöffnete Datei zurück. Ein NULL-Zeigerwert gibt einen Fehler an. Wenn *Dateiname* oder *Modus* **NULL** oder eine leere Zeichenfolge ist, lösen diese Funktionen den ungültigen Parameterhandler aus, der unter [Parametervalidierung](../../c-runtime-library/parameter-validation.md)beschrieben wird. Wenn die Ausführung fortgesetzt werden darf, geben diese Funktionen **NULL** zurück und setzen **errno** auf **EINVAL**.

Weitere Informationen finden Sie unter [errno, _doserrno, _sys_errlist und _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Bemerkungen

Die **fopen-Funktion** öffnet die Datei, die durch *filename*angegeben wird. Standardmäßig wird eine Zeichenfolge mit einem schmalen *Dateinamen* mithilfe der ANSI-Codepage (CP_ACP interpretiert. In Windows-Desktopanwendungen kann dies in die OEM-Codepage (CP_OEMCP) geändert werden, indem Sie die [SetFileApisToOEM](/windows/win32/api/fileapi/nf-fileapi-setfileapistooem) -Funktion verwenden. Sie können die [AreFileApisANSI-Funktion](/windows/win32/api/fileapi/nf-fileapi-arefileapisansi) verwenden, um zu bestimmen, ob *der Dateiname* mithilfe der ANSI oder der Standardmäßigen OEM-Codepage interpretiert wird. **_wfopen** ist eine breitstellige Version von **fopen**; Die Argumente für **_wfopen** sind Zeichenfolgen mit großen Zeichen. Andernfalls verhalten sich **_wfopen** und **fopen** identisch. Die Verwendung **von _wfopen** wirkt sich nicht auf den codierten Zeichensatz aus, der im Dateistream verwendet wird.

**fopen** akzeptiert Pfade, die zum Zeitpunkt der Ausführung auf dem Dateisystem gültig sind. **fopen** akzeptiert UNC-Pfade und -Pfade, die zugeordnete Netzlaufwerke umfassen, solange das System, das den Code ausführt, zum Zeitpunkt der Ausführung Zugriff auf die Freigabe oder das zugeordnete Laufwerk hat. Wenn Sie Pfade für **fopen**erstellen, stellen Sie sicher, dass Laufwerke, Pfade oder Netzwerkfreigaben in der Ausführungsumgebung verfügbar sind. Als Verzeichnistrennzeichen in einem Pfad können Sie entweder den Schrägstrich (/) oder den umgekehrten Schrägstrich (\\) verwenden.

Überprüfen Sie stets den Rückgabewert, um zu ermitteln, ob der Zeiger NULL ist, bevor Sie weitere Vorgänge mit der Datei ausführen. Wenn ein Fehler auftritt, wird die globale Variable **errno** festgelegt und kann verwendet werden, um bestimmte Fehlerinformationen zu erhalten. Weitere Informationen finden Sie unter [errno, _doserrno, _sys_errlist und _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen dazu finden Sie [unter Globaler Status in der CRT](../global-state.md).

## <a name="unicode-support"></a>Unicode-Unterstützung

**fopen** unterstützt Unicode-Dateistreams. Um eine Unicode-Datei zu öffnen, übergeben Sie ein **ccs-Flag,** das die gewünschte Codierung für **fopen**wie folgt angibt.

> **FILE \*fp = fopen("newfile.txt", "rt+, ccs=**_codierung_**");**

Zulässige Werte der *Codierung* sind **UNICODE**, **UTF-8**und **UTF-16LE**.

Wenn eine Datei im Unicode-Modus geöffnet wird, übersetzen Eingabefunktionen die aus der Datei gelesenen Daten in UTF-16-Daten, die als Typ **wchar_t**gespeichert sind. Funktionen, die in eine im Unicode-Modus geöffnete Datei schreiben, erwarten Puffer, die UTF-16-Daten enthalten, die als Typ **wchar_t**gespeichert sind. Wenn eine Datei als UTF-8 kodiert ist, dann werden UTF-16-Daten beim Schreiben in UTF-8 übersetzt, und die UTF-8-kodierten Inhalte der Datei werden beim Lesen in UTF-16 übersetzt. Der Versuch, eine ungerade Anzahl von Bytes im Unicode-Modus zu lesen oder zu schreiben, führt zu einem [Parametervalidierungsfehler](../../c-runtime-library/parameter-validation.md) . Wenn Sie Daten lesen oder schreiben möchten, die in Ihrem Programm als UTF-8 gespeichert sind, verwenden Sie den Text- oder Binärdateienmodus anstelle eines Unicode-Modus. Sie sind für jede erforderliche Kodierungsübersetzung verantwortlich.

Wenn die Datei bereits vorhanden ist und zum Lesen oder Anhängen geöffnet ist, bestimmt die Bytereihenfolge-Marke (BOM), sofern in der Datei vorhanden, die Codierung. Die Stücklistencodierung hat Vorrang vor der Codierung, die durch das **ccs-Flag** angegeben wird. Die **ccs-Codierung** wird nur verwendet, wenn keine Stückliste vorhanden ist oder die Datei eine neue Datei ist.

> [!NOTE]
> Die Stücklistenerkennung gilt nur für Dateien, die im Unicode-Modus geöffnet werden (d. h. durch Übergeben des **ccs-Flags).**

In der folgenden Tabelle werden die Modi zusammengefasst, die für verschiedene **ccS-Flags** verwendet werden, die **fopen-** und Byte-Order-Marken in der Datei angegeben werden.

### <a name="encodings-used-based-on-ccs-flag-and-bom"></a>Verwendete Codierungen auf Grundlage von ccs-Flag und BOM

|ccs-Flagge|Keine BOM (oder neue Datei)|BOM: UTF-8|BOM: UTF-16|
|----------------|----------------------------|-----------------|------------------|
|**Unicode**|**UTF-16LE**|**UTF-8**|**UTF-16LE**|
|**UTF-8**|**UTF-8**|**UTF-8**|**UTF-16LE**|
|**UTF-16LE**|**UTF-16LE**|**UTF-8**|**UTF-16LE**|

In Dateien, die zum Schreiben im Unicode-Modus geöffnet sind, wird automatisch eine BOM geschrieben.

Wenn *der Modus* **"a, ccs=**_codiert"_**"** ist, versucht **fopen** zuerst, die Datei mit Lese- und Schreibzugriff zu öffnen. Ist der Vorgang erfolgreich, liest die Funktion die BOM, um die Codierung für die Datei zu bestimmen. Schlägt der Vorgang fehl, verwendet die Funktion die Standardcodierung für die Datei. In beiden Fällen öffnet **fopen** die Datei dann erneut, indem nur Schreibzugriff verwendet wird. (Dies gilt nur für **den "a"-Modus,** nicht für den **Modus "a+".)**

### <a name="generic-text-routine-mappings"></a>Zuordnung generischer Textroutinen

|TCHAR.H-Routine|_UNICODE und _MBCS nicht definiert.|_MBCS definiert|_UNICODE definiert|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tfopen**|**fopen**|**fopen**|**_wfopen**|

Der *Zeichenkettenmodus* gibt die Art des Zugriffs an, der für die Datei angefordert wird, wie folgt.

|*Modus*|Zugriff|
|-|-|
| **"r"** | Öffnet zum Lesen. Wenn die Datei nicht vorhanden ist oder nicht gefunden werden kann, schlägt der **Fopen-Aufruf** fehl. |
| **"w"** | Öffnet eine leere Datei zum Schreiben. Wenn die angegebene Datei vorhanden ist, wird ihr Inhalt zerstört. |
| **"a"** | Wird vor dem Schreiben neuer Daten in die Datei zum Schreiben am Ende der Datei (Anfügen) geöffnet, ohne die EOF-Markierung (end-of-file, Dateiende) zu entfernen. Erstellt die Datei, wenn sie nicht vorhanden ist. |
| **"r+"** | Öffnet sowohl zum Lesen als auch zum Schreiben. Die Datei muss vorhanden sein. |
| **"w+"** | Öffnet eine leere Datei zum Lesen und Schreiben. Wenn die Datei vorhanden ist, wird ihr Inhalt zerstört. |
| **"a+"** | Öffnet sich zum Lesen und Anfügen. Der Anfügevorgang umfasst das Entfernen der EOF-Markierung, bevor neue Daten in die Datei geschrieben werden. Die EOF-Markierung wird nach Abschluss des Schreibvorgangs nicht wiederhergestellt. Erstellt die Datei, wenn sie nicht vorhanden ist. |

Wenn eine Datei mit dem Zugriffstyp **"a"** oder dem Zugriffstyp **"a+"** geöffnet wird, finden alle Schreibvorgänge am Ende der Datei statt. Der Dateizeiger kann mithilfe von [fseek](fseek-fseeki64.md) oder [reswind](rewind.md)neu positioniert werden, wird jedoch immer wieder an das Ende der Datei verschoben, bevor ein Schreibvorgang ausgeführt wird. Daher können vorhandene Daten nicht überschrieben werden.

Der **"a"-Modus** entfernt die EOF-Markierung nicht, bevor sie an die Datei angehängt wird. Nach dem Anfügen werden durch den MS-DOS-Befehl TYPE nur Daten bis zur ursprünglichen EOF-Markierung angezeigt, aber keine Daten, die an die Datei angefügt wurden. Bevor es an die Datei angehängt wird, entfernt der **Modus "a+"** die EOF-Markierung. Nach dem Anhängen werden mit dem Befehl MS-DOS TYPE alle Daten in der Datei angezeigt. Der **Modus "a+"** ist zum Anfügen an eine Streamdatei erforderlich, die mit der STRG+Z-EOF-Markierung beendet wird.

Wenn der Zugriffstyp **"r+"**, **"w+"** oder **"a+"** angegeben ist, werden sowohl lesen als auch schreiben aktiviert (die Datei soll für "update" geöffnet sein). Wenn Sie jedoch vom Lesevorgang in den Schreibvorgang wechseln, muss die Eingabeoperation eine EOF-Markierung antreffen. Wenn keine EOF-Markierung vorhanden ist, müssen Sie einen zwischenzeitlichen Aufruf einer dateipositionierenden Funktion verwenden. Die Dateipositionierungsfunktionen sind **fsetpos**, [fseek](fseek-fseeki64.md)und [reswind](rewind.md). Wenn Sie vom Schreiben zum Lesen wechseln, müssen Sie einen dazwischenliegenden Aufruf verwenden, um entweder **fflush** oder eine Dateipositionierungsfunktion zu erstellen.

Zusätzlich zu den früheren Werten können die folgenden Zeichen an den *Modus* angehängt werden, um den Übersetzungsmodus für Zeilenumleinenzeichen anzugeben.

|*mode* Modusmodifizierer|Übersetzungsmodus|
|-|-|
| **T** | Öffnen im Textmodus (übersetzt). |
| **B** | Öffnen im binären (unübersetzten) Modus; Übersetzungen mit Wagen-Rücklauf- und Zeilenvorschubzeichen werden unterdrückt. |

Im Textmodus wird STRG+Z als EOF-Zeichen bei der Eingabe interpretiert. In Dateien, die mit **"a+"** zum Lesen/Schreiben geöffnet werden, sucht **fopen** nach einem STRG+Z am Ende der Datei und entfernt sie, wenn möglich. Dies geschieht, weil die Verwendung von [fseek](fseek-fseeki64.md) und **ftell,** um innerhalb einer Datei zu verschieben, die mit STRG+Z endet, dazu führen kann, dass [fseek](fseek-fseeki64.md) sich am Ende der Datei falsch verhält.

Im Textmodus werden Wagen-Rücklauf-Feed-Kombinationen bei der Eingabe in einzeilige Feeds übersetzt, und Zeilenvorschubzeichen werden bei der Ausgabe in Wagen-Rücklauf-Feed-Kombinationen übersetzt. Wenn eine Stream-E/A-Funktion von Unicode im Textmodus (Standard) funktioniert, wird angenommen, dass es sich bei Quell- oder Zielstream um eine Sequenz von Multibytezeichen handelt. Daher konvertieren die Unicode-Streameingabefunktionen Multibytezeichen in Breitzeichen (wie bei einem Aufruf der **mbtowc**-Funktion). Aus demselben Grund konvertieren die Unicode-Streamausgabefunktionen Breitzeichen in Multibytezeichen (wie bei einem Aufruf der **wctomb**-Funktion).

Wenn **t** oder **b** im *Modus*nicht angegeben ist, wird der Standard-Übersetzungsmodus durch die globale Variable [_fmode](../../c-runtime-library/fmode.md)definiert. Wenn dem Argument **t** oder **b** der Vorzeichen vorangestellt ist, schlägt die Funktion fehl und gibt **NULL**zurück.

Weitere Informationen darüber, wie Sie Textmodus und Binärmodus in Unicode und im Multibyte-Stream-E/A verwenden, finden Sie unter [Text and Binary Mode File I/O](../../c-runtime-library/text-and-binary-mode-file-i-o.md) und [Unicode Stream I/O in Text and Binary Modes](../../c-runtime-library/unicode-stream-i-o-in-text-and-binary-modes.md).

Die folgenden Optionen können an den *Modus* angehängt werden, um zusätzliche Verhaltensweisen anzugeben.

|*mode* Modusmodifizierer|Verhalten|
|-|-|
| **C** | Aktivieren Sie das Commit-Flag für den zugeordneten *Dateinamen,* damit der Inhalt des Dateipuffers direkt auf den Datenträger geschrieben wird, wenn entweder **fflush** oder **_flushall** aufgerufen wird. |
| **n** | Setzen Sie das Commit-Flag für den zugeordneten *Dateinamen* auf "no-commit" zurück. Dies ist die Standardoption. Dabei wird auch das globale Commitflag überschrieben, wenn Sie das Programm mit COMMODE.OBJ verknüpfen. Der Standardwert des globalen Commitflags lautet "no-commit", es sei denn, Sie verknüpfen das Programm explizit mit COMMODE.OBJ (siehe [Link Options](../../c-runtime-library/link-options.md)). |
| **N** | Gibt an, dass die Datei nicht von untergeordneten Prozessen geerbt wird. |
| **E** | Gibt an, dass das Zwischenspeichern für den sequenziellen Zugriff vom Datenträger optimiert, aber nicht darauf beschränkt ist. |
| **R** | Gibt an, dass das Zwischenspeichern für den zufälligen Zugriff vom Datenträger optimiert, aber nicht darauf beschränkt ist. |
| **T** | Gibt an, dass eine Datei temporär ist. Wenn möglich, wird sie nicht auf den Datenträger geschrieben. |
| **D** | Gibt an, dass eine Datei temporär ist. Sie wird gelöscht, wenn der letzte Dateizeiger geschlossen wird. |
| **ccs=**_Codierung_ | Gibt den zu verwendenden codierten Zeichensatz (einen von **UTF-8**, **UTF-16LE**oder **UNICODE**) für diese Datei an. Machen Sie keine Angabe, wenn Sie ANSI-Codierung wünschen. |

Gültige Zeichen für die *Moduszeichenfolge,* die in **fopen** und **_fdopen** verwendet wird, entsprechen *oflag-Argumenten,* die in [_open](open-wopen.md) und [_sopen](sopen-wsopen.md)wie folgt verwendet werden.

|Zeichen in *der Moduszeichenfolge*|Äquivalent *zum lag-Wert* für \_open/sopen\_|
|-------------------------------|----------------------------------------------------|
|**Eine**|**\_O\_WRONLY** &#124; ** \_O\_APPEND** (normalerweise ** \_\_O WRONLY** &#124; ** \_O\_CREAT** &#124; ** \_O\_APPEND**)|
|**a+**|**\_O\_RDWR** &#124; ** \_O\_APPEND** (in der Regel ** \_\_O RDWR** &#124; ** \_O\_APPEND** &#124; ** \_O\_CREAT** )|
|**R**|**\_O\_RDONLY**|
|**r+**|**\_O\_RDWR**|
|**w**|**\_O\_WRONLY** (in der Regel ** \_O\_WRONLY** &#124; ** \_O\_CREAT** &#124; ** \_O\_TRUNC**)|
|**w+**|**\_O\_RDWR** (in der Regel ** \_O\_RDWR** &#124; ** \_O\_CREAT** &#124; ** \_O\_TRUNC**)|
|**B**|**\_O\_BINARY**|
|**T**|**\_O\_TEXT**|
|**C**|Keine|
|**n**|Keine|
|**E**|**\_O\_SEQUENTIAL**|
|**R**|**\_O\_RANDOM**|
|**T**|**\_O\_SHORTLIVED**|
|**D**|**\_O\_TEMPORARY**|
|**ccs=UNICODE**|**\_O\_WTEXT**|
|**ccs=UTF-8**|**\_O\_UTF8**|
|**ccs=UTF-16LE**|**\_O\_UTF16**|

Wenn Sie den **RB-Modus** verwenden, müssen Sie den Code nicht portieren, und wenn Sie erwarten, den größten Teil einer großen Datei zu lesen, oder wenn Sie sich keine Sorgen um die Netzwerkleistung machen, sollten Sie auch überlegen, ob Sie win32-Speicherzuordnungsdateien als Option verwenden möchten.

## <a name="requirements"></a>Anforderungen

|Funktion|Erforderlicher Header|
|--------------|---------------------|
|**fopen**|\<stdio.h>|
|**_wfopen**|\<stdio.h> oder \<wchar.h>|

**_wfopen** ist eine Microsoft-Erweiterung. Weitere Informationen zur Kompatibilität finden Sie unter [Kompatibilität](../../c-runtime-library/compatibility.md).

Die *Optionen* **c**, **n**, **t**, **S**, **R**, **T**und **D** sind Microsoft-Erweiterungen für **fopen** und **_fdopen** und sollten nicht dort verwendet werden, wo ANSI-Portabilität gewünscht wird.

## <a name="example-1"></a>Beispiel 1

Das folgende Programm öffnet zwei Dateien.  Es verwendet **fclose,** um die erste Datei zu schließen und **_fcloseall,** um alle verbleibenden Dateien zu schließen.

```C
// crt_fopen.c
// compile with: /W3
// This program opens two files. It uses
// fclose to close the first file and
// _fcloseall to close all remaining files.

#include <stdio.h>

FILE *stream, *stream2;

int main( void )
{
   int numclosed;

   // Open for read (will fail if file "crt_fopen.c" does not exist)
   if( (stream  = fopen( "crt_fopen.c", "r" )) == NULL ) // C4996
   // Note: fopen is deprecated; consider using fopen_s instead
      printf( "The file 'crt_fopen.c' was not opened\n" );
   else
      printf( "The file 'crt_fopen.c' was opened\n" );

   // Open for write
   if( (stream2 = fopen( "data2", "w+" )) == NULL ) // C4996
      printf( "The file 'data2' was not opened\n" );
   else
      printf( "The file 'data2' was opened\n" );

   // Close stream if it is not NULL
   if( stream)
   {
      if ( fclose( stream ) )
      {
         printf( "The file 'crt_fopen.c' was not closed\n" );
      }
   }

   // All other files are closed:
   numclosed = _fcloseall( );
   printf( "Number of files closed by _fcloseall: %u\n", numclosed );
}
```

```Output
The file 'crt_fopen.c' was opened
The file 'data2' was opened
Number of files closed by _fcloseall: 1
```

## <a name="example-2"></a>Beispiel 2

Das folgende Programm erstellt eine Datei (oder überschreibt eine, sofern vorhanden) im Textmodus mit Unicode-Codierung.  Anschließend schreibt es zwei Zeichenfolgen in die Datei und schließt sie. Die Ausgabe ist eine Datei namens _wfopen_test.xml, die die Daten aus dem Ausgangsabschnitt enthält.

```C
// crt__wfopen.c
// compile with: /W3
// This program creates a file (or overwrites one if
// it exists), in text mode using Unicode encoding.
// It then writes two strings into the file
// and then closes the file.

#include <stdio.h>
#include <stddef.h>
#include <stdlib.h>
#include <wchar.h>

#define BUFFER_SIZE 50

int main(int argc, char** argv)
{
    wchar_t str[BUFFER_SIZE];
    size_t  strSize;
    FILE*   fileHandle;

    // Create an the xml file in text and Unicode encoding mode.
    if ((fileHandle = _wfopen( L"_wfopen_test.xml",L"wt+,ccs=UNICODE")) == NULL) // C4996
    // Note: _wfopen is deprecated; consider using _wfopen_s instead
    {
        wprintf(L"_wfopen failed!\n");
        return(0);
    }

    // Write a string into the file.
    wcscpy_s(str, sizeof(str)/sizeof(wchar_t), L"<xmlTag>\n");
    strSize = wcslen(str);
    if (fwrite(str, sizeof(wchar_t), strSize, fileHandle) != strSize)
    {
        wprintf(L"fwrite failed!\n");
    }

    // Write a string into the file.
    wcscpy_s(str, sizeof(str)/sizeof(wchar_t), L"</xmlTag>");
    strSize = wcslen(str);
    if (fwrite(str, sizeof(wchar_t), strSize, fileHandle) != strSize)
    {
        wprintf(L"fwrite failed!\n");
    }

    // Close the file.
    if (fclose(fileHandle))
    {
        wprintf(L"fclose failed!\n");
    }
    return 0;
}
```

## <a name="see-also"></a>Siehe auch

[Stream-E/A](../../c-runtime-library/stream-i-o.md)<br/>
[Interpretation von Multibyte-Zeichensequenzen](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[fclose, _fcloseall](fclose-fcloseall.md)<br/>
[_fdopen, _wfdopen](fdopen-wfdopen.md)<br/>
[ferror](ferror.md)<br/>
[_fileno](fileno.md)<br/>
[freopen, _wfreopen](freopen-wfreopen.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
[_setmode](setmode.md)<br/>
[_sopen, _wsopen](sopen-wsopen.md)<br/>
