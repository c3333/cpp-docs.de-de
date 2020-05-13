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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: d468226028928e3edfe67cc7f9b9eec06e06bd56
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/07/2020
ms.locfileid: "82914891"
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

*Einfügen*<br/>
Dateiname

*mode*<br/>
Art des Zugriffs, der aktiviert ist.

## <a name="return-value"></a>Rückgabewert

Jede dieser Funktionen gibt einen Zeiger auf die geöffnete Datei zurück. Ein NULL-Zeigerwert gibt einen Fehler an. Wenn *filename* oder *Mode* **null** oder eine leere Zeichenfolge ist, wird der Handler für ungültige Parameter von diesen Funktionen auslöst, der in [Parameter Validation (Parameter](../../c-runtime-library/parameter-validation.md)Überprüfung) beschrieben wird. Wenn die weitere Ausführung zugelassen wird, geben diese Funktionen **null** zurück und legen **errno** auf **EINVAL**fest.

Weitere Informationen finden Sie unter [errno, _doserrno, _sys_errlist und _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Hinweise

Die Funktion " **f Open** " öffnet die Datei, die durch *filename*angegeben wird. Standardmäßig wird eine schmale *namens* Zeichenfolge mit der ANSI-Codepage (CP_ACP) interpretiert. In Windows-Desktopanwendungen kann dies in die OEM-Codepage (CP_OEMCP) geändert werden, indem Sie die [SetFileApisToOEM](/windows/win32/api/fileapi/nf-fileapi-setfileapistooem) -Funktion verwenden. Mithilfe der [arefileapisansi](/windows/win32/api/fileapi/nf-fileapi-arefileapisansi) -Funktion können Sie ermitteln, ob *filename* mit der ANSI-Codepage oder der standardmäßigen OEM-Codepage des Systems interpretiert wird. **_wfopen** ist eine breit Zeichen Version von " **f Open**". die Argumente für **_wfopen** sind Zeichen folgen mit breit Zeichen. Andernfalls Verhalten sich **_wfopen** und " **f Open** " identisch. Die Verwendung von **_wfopen** wirkt sich nicht auf den codierten Zeichensatz aus, der im Dateistream verwendet wird.

**fopen** akzeptiert Pfade, die zum Zeitpunkt der Ausführung im Dateisystem gültig sind. **fopen** akzeptiert UNC-Pfade und Pfade mit zugeordneten Netzlaufwerken, solange das System, das den Code ausführt, zum Zeitpunkt der Ausführung Zugriff auf die Freigabe oder das zugeordnete Laufwerk hat. Stellen Sie beim Erstellen von Pfaden für " **f Open**" sicher, dass Laufwerke, Pfade oder Netzwerkfreigaben in der Ausführungsumgebung verfügbar sind. Als Verzeichnistrennzeichen in einem Pfad können Sie entweder den Schrägstrich (/) oder den umgekehrten Schrägstrich (\\) verwenden.

Überprüfen Sie stets den Rückgabewert, um zu ermitteln, ob der Zeiger NULL ist, bevor Sie weitere Vorgänge mit der Datei ausführen. Wenn ein Fehler auftritt, wird die globale Variable **errno** festgelegt und kann verwendet werden, um bestimmte Fehlerinformationen abzurufen. Weitere Informationen finden Sie unter [errno, _doserrno, _sys_errlist und _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen hierzu finden Sie unter [globaler Status in der CRT](../global-state.md).

## <a name="unicode-support"></a>Unicode-Unterstützung

" **f Open** " unterstützt Unicode-Dateistreams. Um eine Unicode-Datei zu öffnen, übergeben Sie ein **CCS** -Flag, das die gewünschte Codierung angibt, wie folgt an **fopen**.

> **Datei \*FP = f Open ("newFile. txt", "RT +, CCS =**_Encoding_**");**

Zulässige *Codierungs* Werte sind **Unicode**, **UTF-8**und **UTF-16LE**.

Wenn eine Datei im Unicode-Modus geöffnet wird, übersetzen Eingabefunktionen die aus der Datei gelesenen Daten in UTF-16-Daten, die als Typ **wchar_t**gespeichert werden. Funktionen, die in eine im Unicode-Modus geöffnete Datei schreiben, erwarten Puffer, die UTF-16-Daten enthalten, die als Typ **wchar_t**gespeichert sind. Wenn eine Datei als UTF-8 kodiert ist, dann werden UTF-16-Daten beim Schreiben in UTF-8 übersetzt, und die UTF-8-kodierten Inhalte der Datei werden beim Lesen in UTF-16 übersetzt. Der Versuch, eine ungerade Anzahl von Bytes im Unicode-Modus zu lesen oder zu schreiben, führt zu einem [Parametervalidierungsfehler](../../c-runtime-library/parameter-validation.md) . Wenn Sie Daten lesen oder schreiben möchten, die in Ihrem Programm als UTF-8 gespeichert sind, verwenden Sie den Text- oder Binärdateienmodus anstelle eines Unicode-Modus. Sie sind für jede erforderliche Kodierungsübersetzung verantwortlich.

Wenn die Datei bereits vorhanden ist und zum Lesen oder Anhängen geöffnet ist, bestimmt die Bytereihenfolge-Marke (BOM), sofern in der Datei vorhanden, die Codierung. Die BOM-Codierung hat Vorrang vor der durch das **CCS** -Flag angegebenen Codierung. Die **CCS** -Codierung wird nur verwendet, wenn keine BOM vorhanden ist oder es sich um eine neue Datei handelt.

> [!NOTE]
> Die BOM-Erkennung gilt nur für Dateien, die im Unicode-Modus geöffnet sind (d. h. durch Übergeben des **CCS** -Flags).

In der folgenden Tabelle werden die Modi zusammengefasst, die für verschiedene **CCS** -Flags verwendet werden, die für **fopen** und Byte Reihenfolge Marken in der Datei angegeben sind.

### <a name="encodings-used-based-on-ccs-flag-and-bom"></a>Verwendete Codierungen auf Grundlage von ccs-Flag und BOM

|CCS-Flag|Keine BOM (oder neue Datei)|BOM: UTF-8|BOM: UTF-16|
|----------------|----------------------------|-----------------|------------------|
|**UNICODE**|**UTF-16LE**|**UTF-8**|**UTF-16LE**|
|**UTF-8**|**UTF-8**|**UTF-8**|**UTF-16LE**|
|**UTF-16LE**|**UTF-16LE**|**UTF-8**|**UTF-16LE**|

In Dateien, die zum Schreiben im Unicode-Modus geöffnet sind, wird automatisch eine BOM geschrieben.

Wenn *mode* der Modus **"a, CCS =**_Encoding_**"** ist, versucht **fopen** zuerst, die Datei mit Lese-und Schreibzugriff zu öffnen. Ist der Vorgang erfolgreich, liest die Funktion die BOM, um die Codierung für die Datei zu bestimmen. Schlägt der Vorgang fehl, verwendet die Funktion die Standardcodierung für die Datei. In jedem Fall wird die Datei von **fopen** erneut mit Schreib geschütztem Zugriff geöffnet. (Dies gilt nur für den Modus **"a"** , nicht für den Modus **"+ +"** ).

### <a name="generic-text-routine-mappings"></a>Zuordnung generischer Textroutinen

|TCHAR.H-Routine|_UNICODE und _MBCS nicht definiert.|_MBCS definiert|_UNICODE definiert|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tfopen**|**fopen**|**fopen**|**_wfopen**|

Der Zeichen folgen *Modus* gibt die Art des Zugriffs, der für die Datei angefordert wird, wie folgt an.

|*mode*|Zugriff|
|-|-|
| **r** | Öffnet zum Lesen. Wenn die Datei nicht vorhanden ist oder nicht gefunden werden kann, schlägt der **fopen** -Befehl fehl. |
| **Löw** | Öffnet eine leere Datei zum Schreiben. Wenn die angegebene Datei vorhanden ist, wird ihr Inhalt zerstört. |
| **ein** | Wird vor dem Schreiben neuer Daten in die Datei zum Schreiben am Ende der Datei (Anfügen) geöffnet, ohne die EOF-Markierung (end-of-file, Dateiende) zu entfernen. Erstellt die Datei, wenn sie nicht vorhanden ist. |
| **"r +"** | Öffnet sowohl zum Lesen als auch zum Schreiben. Die Datei muss vorhanden sein. |
| **"w +"** | Öffnet eine leere Datei zum Lesen und Schreiben. Wenn die Datei vorhanden ist, wird ihr Inhalt zerstört. |
| **"a +"** | Öffnet sich zum Lesen und Anfügen. Der Anfügevorgang umfasst das Entfernen der EOF-Markierung, bevor neue Daten in die Datei geschrieben werden. Die EOF-Markierung wird nach Abschluss des Schreibvorgangs nicht wiederhergestellt. Erstellt die Datei, wenn sie nicht vorhanden ist. |

Wenn eine Datei mit dem Zugriffstyp **"a"** oder dem Zugriffstyp **"a +"** geöffnet wird, erfolgen alle Schreibvorgänge am Ende der Datei. Der Dateizeiger kann mithilfe von [fseek](fseek-fseeki64.md) oder [Rewind](rewind.md)neu positioniert werden, wird jedoch immer wieder zurück an das Ende der Datei verschoben, bevor ein Schreibvorgang durchgeführt wird. Daher können vorhandene Daten nicht überschrieben werden.

Der **"a"** -Modus entfernt die EOF-Markierung nicht, bevor Sie an die Datei angefügt wird. Nach dem Anfügen werden durch den MS-DOS-Befehl TYPE nur Daten bis zur ursprünglichen EOF-Markierung angezeigt, aber keine Daten, die an die Datei angefügt wurden. Bevor Sie an die Datei angefügt wird, wird die EOF-Markierung durch den Modus **"a +"** entfernt. Nach dem Anhängen werden mit dem Befehl MS-DOS TYPE alle Daten in der Datei angezeigt. Der Modus **"a +"** ist zum Anfügen an eine streamdatei erforderlich, die mit der EOF-Markierung STRG + Z beendet wird.

Wenn der Zugriffstyp **"r +"**, **"w +"** oder **"a +** " angegeben wird, sind sowohl Lese-als auch Schreibvorgänge aktiviert (die Datei ist zum Aktualisieren geöffnet). Wenn Sie jedoch vom Lesevorgang in den Schreibvorgang wechseln, muss die Eingabeoperation eine EOF-Markierung antreffen. Wenn keine EOF-Markierung vorhanden ist, müssen Sie einen zwischenzeitlichen Aufruf einer dateipositionierenden Funktion verwenden. Die Datei Positionierungsfunktionen sind " **f**", " [f Seek](fseek-fseeki64.md)" und " [Rewind](rewind.md)". Wenn Sie vom Schreibvorgang in den Lesevorgang wechseln, müssen **Sie entweder einen** zwischenzeitlichen oder einen zwischenzeitlichen aufzurufenden oder zu einer Datei positionierenden Funktion verwenden.

Zusätzlich zu den früheren Werten können die folgenden Zeichen an den- *Modus* angehängt werden, um den Übersetzungsmodus für Zeilen Umleitungs Zeichen anzugeben.

|*mode* modusmodifizierer|Übersetzungsmodus|
|-|-|
| **Bund** | Öffnen im Textmodus (übersetzt). |
| **b** | Im binären (nicht übersetzten) Modus öffnen; Übersetzungen mit Wagen Rücklauf-und Zeilenvorschub Zeichen werden unterdrückt. |

Im Textmodus wird STRG + Z bei der Eingabe als EOF-Zeichen interpretiert. In Dateien, die für das Lesen/Schreiben mithilfe von **"a +"** geöffnet sind, prüft " **f** ", ob am Ende der Datei STRG + Z angezeigt wird, und entfernt diese, wenn dies möglich ist. Dies geschieht, da die Verwendung von [fseek](fseek-fseeki64.md) und **ftell** zum Verschieben innerhalb einer Datei, die mit STRG + Z endet, dazu führen kann, dass sich [fseek](fseek-fseeki64.md) in der Nähe des Datei Endes nicht ordnungsgemäß verhält.

Im Textmodus werden Wagen Rücklauf-und Zeilenvorschub-Kombinationen bei Eingabe in einzeilige Feeds übersetzt, und Zeilenvorschub Zeichen werden bei der Ausgabe in Wagen Rücklauf-Zeilenvorschub-Kombinationen übersetzt. Wenn eine Stream-E/A-Funktion von Unicode im Textmodus (Standard) funktioniert, wird angenommen, dass es sich bei Quell- oder Zielstream um eine Sequenz von Multibytezeichen handelt. Daher konvertieren die Unicode-Streameingabefunktionen Multibytezeichen in Breitzeichen (wie bei einem Aufruf der **mbtowc**-Funktion). Aus demselben Grund konvertieren die Unicode-Streamausgabefunktionen Breitzeichen in Multibytezeichen (wie bei einem Aufruf der **wctomb**-Funktion).

Wenn " **t** " oder " **b** " im- *Modus*nicht angegeben wird, wird der Standard Übersetzungsmodus durch die globale Variable [_fmode](../../c-runtime-library/fmode.md)definiert. Wenn **t** oder **b** dem Argument vorangestellt wird, schlägt die Funktion fehl und gibt **null**zurück.

Weitere Informationen darüber, wie Sie Textmodus und Binärmodus in Unicode und im Multibyte-Stream-E/A verwenden, finden Sie unter [Text and Binary Mode File I/O](../../c-runtime-library/text-and-binary-mode-file-i-o.md) und [Unicode Stream I/O in Text and Binary Modes](../../c-runtime-library/unicode-stream-i-o-in-text-and-binary-modes.md).

Die folgenden Optionen können an den- *Modus* angehängt werden, um zusätzliche Verhalten anzugeben.

|*mode* modusmodifizierer|Verhalten|
|-|-|
| **scher** | Aktivieren Sie das commitflag für den zugeordneten *Dateinamen* , damit der Inhalt des Datei Puffers direkt auf den Datenträger geschrieben wird, wenn entweder **fflush** oder **_flushall** aufgerufen wird. |
| **n** | Setzen Sie das commitflag für den zugeordneten *Dateinamen* auf "No-Commit" zurück. Dies ist die Standardeinstellung. Dabei wird auch das globale Commitflag überschrieben, wenn Sie das Programm mit COMMODE.OBJ verknüpfen. Der Standardwert des globalen Commitflags lautet "no-commit", es sei denn, Sie verknüpfen das Programm explizit mit COMMODE.OBJ (siehe [Link Options](../../c-runtime-library/link-options.md)). |
| **Nr** | Gibt an, dass die Datei nicht von untergeordneten Prozessen geerbt wird. |
| **Hymnen** | Gibt an, dass das Zwischenspeichern für den sequenziellen Zugriff vom Datenträger optimiert, aber nicht darauf beschränkt ist. |
| **R** | Gibt an, dass das Zwischenspeichern für den zufälligen Zugriff vom Datenträger optimiert, aber nicht darauf beschränkt ist. |
| **T** | Gibt an, dass eine Datei temporär ist. Wenn möglich, wird sie nicht auf den Datenträger geschrieben. |
| **D** | Gibt an, dass eine Datei temporär ist. Sie wird gelöscht, wenn der letzte Dateizeiger geschlossen wird. |
| **CCS =**_Codierung_ | Gibt den codierten Zeichensatz an, der für diese Datei verwendet werden soll (einer der **UTF-8**, **UTF-16LE**oder **Unicode**). Machen Sie keine Angabe, wenn Sie ANSI-Codierung wünschen. |

Gültige Zeichen für die *moduszeichenfolge, die in* **fopen** verwendet wird, und **_fdopen** entsprechen *Oflag* -Argumenten, die wie folgt in [_open](open-wopen.md) und [_sopen](sopen-wsopen.md)verwendet werden.

|Zeichen in der *Mode* -Zeichenfolge|Entsprechender *Oflag* -Wert \_für Open\_/sopen|
|-------------------------------|----------------------------------------------------|
|**ein**|**\_O\_wronly** &#124; ** \_o\_Append** (in der Regel ** \_o\_wronly** &#124; ** \_o\_** - ** \_Anweisung\_&#124; o Append**)|
|**a +**|**\_O\_rdwr** &#124; ** \_o\_Append** (i. d. ** \_r. o\_rdwr** &#124; ** \_o\_Append** &#124; ** \_o\_| anfüat** )|
|**r**|**\_O\_rdonly**|
|**r +**|**\_O\_rdwr**|
|**w**|**\_O\_wronly** (in der Regel ** \_\_o wronly** &#124; ** \_o\_** - ** \_&#124;\_o trunc**)|
|**w +**|**\_O\_rdwr** (in der Regel ** \_o\_rdwr** &#124; ** \_o\_** &#124; ** \_o\_trunc**)|
|**b**|**\_O\_-Binärdatei**|
|**Bund**|**\_O\_-Text**|
|**scher**|Keine|
|**n**|Keine|
|**Hymnen**|**\_\_sequenziell**|
|**R**|**\_O\_Random**|
|**T**|**\_O\_kurzlebig**|
|**D**|**\_O\_temporär**|
|**CCS = Unicode**|**\_O\_wtext**|
|**CCS = UTF-8**|**\_O\_UTF8**|
|**CCS = UTF-16LE**|**\_O\_UTF16**|

Wenn Sie den **RB** -Modus verwenden, müssen Sie Ihren Code nicht portieren. Wenn Sie davon ausgehen, den Großteil einer großen Datei zu lesen, oder die Netzwerkleistung nicht relevant ist, können Sie auch überlegen, ob Sie die Speicher Abbild-Win32-Dateien als Option verwenden möchten.

## <a name="requirements"></a>Anforderungen

|Funktion|Erforderlicher Header|
|--------------|---------------------|
|**fopen**|\<stdio.h>|
|**_wfopen**|\<stdio.h> oder \<wchar.h>|

**_wfopen** ist eine Microsoft-Erweiterung. Weitere Informationen zur Kompatibilität finden Sie unter [Kompatibilität](../../c-runtime-library/compatibility.md).

Die *Optionen "* **c**", " **n**", " **t** **", "** **R**", " **t**" und " **D** " sind Microsoft-Erweiterungen für " **f Open** " und " **_fdopen** .

## <a name="example-1"></a>Beispiel 1

Das folgende Programm öffnet zwei Dateien.  Er verwendet **fclose** , um die erste Datei zu schließen, und **_fcloseall** , um alle verbleibenden Dateien zu schließen.

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

## <a name="see-also"></a>Weitere Informationen

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
