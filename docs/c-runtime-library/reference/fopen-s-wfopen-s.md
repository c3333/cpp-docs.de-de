---
title: fopen_s, _wfopen_s
ms.date: 4/2/2020
api_name:
- _wfopen_s
- fopen_s
- _o__wfopen_s
- _o_fopen_s
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
- fopen_s
- _tfopen_s
- _wfopen_s
helpviewer_keywords:
- _wfopen_s function
- opening files, for file I/O
- _tfopen_s function
- tfopen_s function
- wfopen_s function
- fopen_s function
- Unicode [C++], creating files
- Unicode [C++], writing files
- files [C++], opening
- Unicode [C++], files
ms.assetid: c534857e-39ee-4a3f-bd26-dfe551ac96c3
ms.openlocfilehash: 80d04e75637cfab9795bf5dfb9da9786cf4ebd71
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81346490"
---
# <a name="fopen_s-_wfopen_s"></a>fopen_s, _wfopen_s

Öffnet eine Datei. Diese Versionen von [fopen, _wfopen](fopen-wfopen.md) enthalten Sicherheitserweiterungen, wie unter [Sicherheitserweiterungen in der CRT](../../c-runtime-library/security-features-in-the-crt.md) beschrieben.

## <a name="syntax"></a>Syntax

```C
errno_t fopen_s(
   FILE** pFile,
   const char *filename,
   const char *mode
);
errno_t _wfopen_s(
   FILE** pFile,
   const wchar_t *filename,
   const wchar_t *mode
);
```

### <a name="parameters"></a>Parameter

*pFile*<br/>
Ein Zeiger auf den Dateizeiger, der den Zeiger auf die geöffnete Datei erhält.

*Dateiname*<br/>
Dateiname.

*Modus*<br/>
Zugriffstyp zulässig.

## <a name="return-value"></a>Rückgabewert

Null, wenn erfolgreich, ein Fehlercode, wenn ein Fehler auftritt. Weitere Informationen zu diesen Fehlercodes finden Sie unter [_doserrno, errno, _sys_errlist und _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

### <a name="error-conditions"></a>Fehlerbedingungen

|*pFile*|*Dateiname*|*Modus*|Rückgabewert|Inhalt von *pFile*|
|-------------|----------------|------------|------------------|------------------------|
|**Null**|any|any|**Einval**|unverändert|
|any|**Null**|any|**Einval**|unverändert|
|any|any|**Null**|**Einval**|unverändert|

## <a name="remarks"></a>Bemerkungen

Dateien, die von **fopen_s** und **_wfopen_s** geöffnet werden, sind nicht sharable. Wenn Sie eine Datei sharable benötigen, verwenden Sie [_fsopen, _wfsopen](fsopen-wfsopen.md) mit der entsprechenden Freigabemoduskonstante, z. B. **_SH_DENYNO** für Lese-/Schreibfreigabe.

Die **fopen_s-Funktion** öffnet die Datei, die durch *filename*angegeben ist. **_wfopen_s** ist eine breitgefächerte Version von **fopen_s**; Die Argumente für **_wfopen_s** sind Zeichenfolgen mit großen Zeichen. **_wfopen_s** und **fopen_s** verhalten sich ansonsten gleich.

**fopen_s** akzeptiert Pfade, die zum Zeitpunkt der Ausführung auf dem Dateisystem gültig sind. UNC-Pfade und -Pfade, die zugeordnete Netzlaufwerke umfassen, werden von **fopen_s** akzeptiert, solange das System, das den Code ausführt, zum Zeitpunkt der Ausführung Zugriff auf die Freigabe oder das zugeordnete Netzlaufwerk hat. Wenn Sie Pfade für **fopen_s**erstellen, sollten Sie keine Annahmen über die Verfügbarkeit von Laufwerken, Pfaden oder Netzwerkfreigaben in der Ausführungsumgebung treffen. Als Verzeichnistrennzeichen in einem Pfad können Sie entweder den Schrägstrich (/) oder den umgekehrten Schrägstrich (\\) verwenden.

Diese Funktionen überprüfen ihre Parameter. Wenn *pFile*, *filename*oder *mode* ein NULL-Zeiger ist, generieren diese Funktionen eine ungültige Parameterausnahme, wie unter [Parametervalidierung](../../c-runtime-library/parameter-validation.md)beschrieben.

Überprüfen Sie stets den Rückgabewert, um festzustellen, ob die Funktion erfolgreich war, bevor Sie mit der Datei andere Vorgänge ausführen. Wenn ein Fehler auftritt, wird der Fehlercode zurückgegeben und die globale Variable **errno** festgelegt. Weitere Informationen finden Sie unter [errno, _doserrno, _sys_errlist und _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen dazu finden Sie [unter Globaler Status in der CRT](../global-state.md).

## <a name="unicode-support"></a>Unicode-Unterstützung

**fopen_s** unterstützt Unicode-Dateistreams. Um eine neue oder vorhandene Unicode-Datei zu öffnen, übergeben Sie ein *ccs-Flag,* das die gewünschte Codierung an **fopen_s**angibt:

**fopen_s(&fp, "newfile.txt", "rw, ccs=**_codierung_**");**

Zulässige Werte der *Codierung* sind **UNICODE**, **UTF-8**und **UTF-16LE**. Wenn für die *Codierung*kein Wert angegeben ist, verwendet **fopen_s** ANSI-Codierung.

Wenn die Datei bereits vorhanden ist und zum Lesen oder Anhängen geöffnet ist, bestimmt die Bytereihenfolge-Marke (BOM), sofern in der Datei vorhanden, die Codierung. Die Stücklistencodierung hat Vorrang vor der Codierung, die durch das *ccs-Flag* angegeben wird. Die *ccs-Codierung* wird nur verwendet, wenn keine Stückliste vorhanden ist oder wenn es sich bei der Datei um eine neue Datei handelt.

> [!NOTE]
> Die Stücklistenerkennung gilt nur für Dateien, die im Unicode-Modus geöffnet werden. das heißt, indem Sie die *ccs-Flagge* übergeben.

In der folgenden Tabelle werden die Modi für verschiedene *ccS-Flags* zusammengefasst, **die fopen_s** und Byte Order Marks in der Datei angezeigt werden.

### <a name="encodings-used-based-on-ccs-flag-and-bom"></a>Verwendete Codierungen auf Grundlage von ccs-Flag und BOM

|ccs-Flagge|Keine BOM (oder neue Datei)|BOM: UTF-8|BOM: UTF-16|
|----------------|----------------------------|-----------------|------------------|
|**Unicode**|**UTF-16LE**|**UTF-8**|**UTF-16LE**|
|**UTF-8**|**UTF-8**|**UTF-8**|**UTF-16LE**|
|**UTF-16LE**|**UTF-16LE**|**UTF-8**|**UTF-16LE**|

In Dateien, die zum Schreiben im Unicode-Modus geöffnet werden, wird automatisch eine BOM geschrieben.

Wenn *der Modus* **"a, ccs=**_codiert_**"** ist, versucht **fopen_s** zuerst, die Datei sowohl mit Lese- als auch Schreibzugriff zu öffnen. Ist der Vorgang erfolgreich, liest die Funktion die BOM, um die Codierung für die Datei zu bestimmen. Schlägt der Vorgang fehl, verwendet die Funktion die Standardcodierung für die Datei. In beiden Fällen **öffnet fopen_s** die Datei dann erneut mit Schreibzugriff. (Dies gilt nur für **einen** Modus, nicht **für a+**.)

### <a name="generic-text-routine-mappings"></a>Zuordnung generischer Textroutinen

|TCHAR.H-Routine|_UNICODE und _MBCS nicht definiert.|_MBCS definiert|_UNICODE definiert|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tfopen_s**|**fopen_s**|**fopen_s**|**_wfopen_s**|

Der *Zeichenkettenmodus* gibt die Art des Zugriffs an, der für die Datei angefordert wird, wie folgt.

|*Modus*|Zugriff|
|-|-|
| **"r"** | Öffnet zum Lesen. Wenn die Datei nicht vorhanden ist oder nicht gefunden werden kann, schlägt der **fopen_s-Aufruf** fehl. |
| **"w"** | Öffnet eine leere Datei zum Schreiben. Wenn die angegebene Datei vorhanden ist, wird ihr Inhalt zerstört. |
| **"a"** | Wird vor dem Schreiben neuer Daten in die Datei zum Schreiben am Ende der Datei (Anfügen) geöffnet, ohne die EOF-Markierung (end-of-file, Dateiende) zu entfernen. Erstellt die Datei, wenn sie nicht vorhanden ist. |
| **"r+"** | Öffnet sowohl zum Lesen als auch zum Schreiben. Die Datei muss vorhanden sein. |
| **"w+"** | Öffnet eine leere Datei zum Lesen und Schreiben. Wenn die Datei vorhanden ist, wird ihr Inhalt zerstört. |
| **"a+"** | Öffnet sich zum Lesen und Anfügen. Der Anfügevorgang umfasst das Entfernen der EOF-Markierung, bevor neue Daten in die Datei geschrieben werden. Die EOF-Markierung wird nach Abschluss des Schreibvorgangs nicht wiederhergestellt. Erstellt die Datei, wenn sie nicht vorhanden ist. |

Wenn eine Datei mit dem Zugriffstyp **"a"** oder **"a+"** geöffnet wird, werden alle Schreibvorgänge am Ende der Datei ausgeführt. Der Dateizeiger kann mithilfe von [fseek](fseek-fseeki64.md) oder [reswind](rewind.md)neu positioniert werden, aber er wird immer wieder an das Ende der Datei verschoben, bevor ein Schreibvorgang ausgeführt wird, sodass vorhandene Daten nicht überschrieben werden können.

Der **"a"-Modus** entfernt die EOF-Markierung nicht, bevor sie an die Datei angehängt wird. Nach dem Anfügen werden durch den MS-DOS-Befehl TYPE nur Daten bis zur ursprünglichen EOF-Markierung angezeigt, aber keine Daten, die an die Datei angefügt wurden. Der **Modus "a+"** entfernt die EOF-Markierung, bevor sie an die Datei angehängt wird. Nach dem Anhängen werden mit dem Befehl MS-DOS TYPE alle Daten in der Datei angezeigt. Der **Modus "a+"** ist erforderlich, um eine Streamdatei anzuhängen, die mit der STRG+Z-EOF-Markierung beendet wird.

Wenn der Zugriffstyp **"r+"**, **"w+"** oder **"a+"** angegeben ist, sind sowohl Lesen als auch Schreiben zulässig. (Die Datei soll für "Update" geöffnet sein.) Wenn Sie jedoch vom Lesen zum Schreiben wechseln, muss der Eingabevorgang auf einen EOF-Marker stoßen. Wenn keine EOF-Markierung vorhanden ist, müssen Sie einen zwischenzeitlichen Aufruf einer dateipositionierenden Funktion verwenden. Die Dateipositionierungsfunktionen sind **fsetpos**, [fseek](fseek-fseeki64.md)und [reswind](rewind.md). Wenn Sie vom Schreiben zum Lesen wechseln, müssen Sie einen dazwischenliegenden Aufruf verwenden, um entweder **fflush** oder eine Dateipositionierungsfunktion zu erstellen.

Zusätzlich zu den oben genannten Werten können die folgenden Zeichen in den *Modus* einbezogen werden, um den Übersetzungsmodus für Zeilenumleinenzeichen anzugeben:

|*mode* Modusmodifizierer|Übersetzungsmodus|
|-|-|
| **T** | Öffnen im Textmodus (übersetzt). |
| **B** | Öffnen im binären (unübersetzten) Modus; Übersetzungen mit Wagen-Rücklauf- und Zeilenvorschubzeichen werden unterdrückt. |

Im Textmodus (übersetzt) wird STRG+Z bei der Eingabe als Dateiende zeichen interpretiert. In Dateien, die zum Lesen/Schreiben mit **"a+"** geöffnet werden, **sucht fopen_s** nach einem STRG+Z am Ende der Datei und entfernt sie, wenn möglich. Dies geschieht, weil die Verwendung von [fseek](fseek-fseeki64.md) und **ftell,** um innerhalb einer Datei zu verschieben, die mit einem STRG+Z endet, dazu führen kann, dass [fseek](fseek-fseeki64.md) sich am Ende der Datei falsch verhält.

Außerdem werden im Textmodus Wagenrücklauf-Feed-Kombinationen bei der Eingabe in einzeilige Feeds übersetzt, und Zeilenvorschubzeichen werden bei der Ausgabe in Wagen-Rücklauf-Feed-Kombinationen übersetzt. Wenn eine Stream-E/A-Funktion von Unicode im Textmodus (Standard) funktioniert, wird angenommen, dass es sich bei Quell- oder Zielstream um eine Sequenz von Multibytezeichen handelt. Daher konvertieren die Unicode-Streameingabefunktionen Multibytezeichen in Breitzeichen (wie bei einem Aufruf der **mbtowc**-Funktion). Aus demselben Grund konvertieren die Unicode-Streamausgabefunktionen Breitzeichen in Multibytezeichen (wie bei einem Aufruf der **wctomb**-Funktion).

Wenn **t** oder **b** im *Modus*nicht angegeben ist, wird der Standard-Übersetzungsmodus durch die globale Variable [_fmode](../../c-runtime-library/fmode.md)definiert. Wenn dem Argument **t** oder **b** der Vorzeichen vorangestellt ist, schlägt die Funktion fehl und gibt **NULL**zurück.

Weitere Informationen zur Anwendung von Text- und Binärmodi in Unicode- und Multibyte-Stream-E/A finden Sie unter [Text- und Binärmodus-Datei-E/A](../../c-runtime-library/text-and-binary-mode-file-i-o.md) und [Unicode-Stream-E/A in Text- und Binärmodi](../../c-runtime-library/unicode-stream-i-o-in-text-and-binary-modes.md).

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

Gültige Zeichen für die in **fopen_s** verwendete *Moduszeichenfolge* und [_fdopen](fdopen-wfdopen.md) entsprechen den in [_open](open-wopen.md) und [_sopen](sopen-wsopen.md)verwendeten *oflag-Argumenten* wie folgt.

|Zeichen in *der Moduszeichenfolge*|Äquivalent *des lag-Wertes* für _open/_sopen|
|-------------------------------|----------------------------------------------------|
|**Eine**|**_O_WRONLY** &#124; **_O_APPEND** (normalerweise **_O_WRONLY** &#124; **_O_CREAT &#124;**** _O_APPEND**)|
|**a+**|**_O_RDWR** &#124; **_O_APPEND** (in der Regel **_O_RDWR &#124;** _O_APPEND **&#124; &#124;** **_O_CREAT)**|
|**R**|**_O_RDONLY**|
|**r+**|**_O_RDWR**|
|**w**|**_O_WRONLY** (in der Regel _O_WRONLY _O_CREAT **&#124;**** _O_TRUNC**) **&#124;**|
|**w+**|**_O_RDWR** (in der Regel **_O_RDWR** _O_CREAT **&#124;** **_O_TRUNC** _O_TRUNC) &#124;|
|**B**|**_O_BINARY**|
|**T**|**_O_TEXT**|
|**C**|Keine|
|**n**|Keine|
|**E**|**_O_SEQUENTIAL**|
|**R**|**_O_RANDOM**|
|**T**|**_O_SHORTLIVED**|
|**D**|**_O_TEMPORARY**|
|**ccs=UNICODE**|**_O_WTEXT**|
|**ccs=UTF-8**|**_O_UTF8**|
|**ccs=UTF-16LE**|**_O_UTF16**|

Wenn Sie den **RB-Modus** verwenden, Ihren Code nicht portieren müssen und erwarten, einen Großteil der Datei zu lesen und/oder sich nicht um die Netzwerkleistung zu kümmern, können auch die mit dem Speicher zugeordneten Win32-Dateien eine Option sein.

## <a name="requirements"></a>Anforderungen

|Funktion|Erforderlicher Header|
|--------------|---------------------|
|**fopen_s**|\<stdio.h>|
|**_wfopen_s**|\<stdio.h> oder \<wchar.h>|

Zusätzliche Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Bibliotheken

Alle Versionen [C-Laufzeitbibliotheken](../../c-runtime-library/crt-library-features.md).

Die *Optionen* **c**, **n**und **t** sind Microsoft-Erweiterungen für **fopen_s** und [_fdopen](fdopen-wfdopen.md) und sollten nicht dort verwendet werden, wo DIE ANSI-Portabilität gewünscht wird.

## <a name="example"></a>Beispiel

```C
// crt_fopen_s.c
// This program opens two files. It uses
// fclose to close the first file and
// _fcloseall to close all remaining files.

#include <stdio.h>

FILE *stream, *stream2;

int main( void )
{
   errno_t err;

   // Open for read (will fail if file "crt_fopen_s.c" does not exist)
   err  = fopen_s( &stream, "crt_fopen_s.c", "r" );
   if( err == 0 )
   {
      printf( "The file 'crt_fopen_s.c' was opened\n" );
   }
   else
   {
      printf( "The file 'crt_fopen_s.c' was not opened\n" );
   }

   // Open for write
   err = fopen_s( &stream2, "data2", "w+" );
   if( err == 0 )
   {
      printf( "The file 'data2' was opened\n" );
   }
   else
   {
      printf( "The file 'data2' was not opened\n" );
   }

   // Close stream if it is not NULL
   if( stream )
   {
      err = fclose( stream );
      if ( err == 0 )
      {
         printf( "The file 'crt_fopen_s.c' was closed\n" );
      }
      else
      {
         printf( "The file 'crt_fopen_s.c' was not closed\n" );
      }
   }

   // All other files are closed:
   int numclosed = _fcloseall( );
   printf( "Number of files closed by _fcloseall: %u\n", numclosed );
}
```

```Output
The file 'crt_fopen_s.c' was opened
The file 'data2' was opened
Number of files closed by _fcloseall: 1
```

## <a name="see-also"></a>Siehe auch

[Stream-E/A](../../c-runtime-library/stream-i-o.md)<br/>
[fclose, _fcloseall](fclose-fcloseall.md)<br/>
[_fdopen, _wfdopen](fdopen-wfdopen.md)<br/>
[ferror](ferror.md)<br/>
[_fileno](fileno.md)<br/>
[freopen, _wfreopen](freopen-wfreopen.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
[_setmode](setmode.md)<br/>
