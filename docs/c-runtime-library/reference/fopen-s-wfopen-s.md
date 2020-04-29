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
ms.openlocfilehash: f18b04cadfa80d7e0be193bbd552efe8486eeeda
ms.sourcegitcommit: fcc3aeb271449f8be80348740cffef39ba543407
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/29/2020
ms.locfileid: "82538605"
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

*Einfügen*<br/>
Dateiname.

*mode*<br/>
Zugriffstyp zulässig.

## <a name="return-value"></a>Rückgabewert

Null, wenn erfolgreich, ein Fehlercode, wenn ein Fehler auftritt. Weitere Informationen zu diesen Fehlercodes finden Sie unter [_doserrno, errno, _sys_errlist und _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

### <a name="error-conditions"></a>Fehlerbedingungen

|*pFile*|*Einfügen*|*mode*|Rückgabewert|Inhalt von *Pfile*|
|-------------|----------------|------------|------------------|------------------------|
|**NULL**|any|any|**Eingabe**|unverändert|
|any|**NULL**|any|**Eingabe**|unverändert|
|any|any|**NULL**|**Eingabe**|unverändert|

## <a name="remarks"></a>Bemerkungen

Dateien, die von **fopen_s** und **_wfopen_s** geöffnet werden, können nicht freigegeben werden. Wenn eine Datei freigegeben werden muss, verwenden Sie [_fsopen _wfsopen](fsopen-wfsopen.md) mit der entsprechenden freigabemoduskonstante, z. –. **_SH_DENYNO** für die Lese-/Schreibfreigabe.

Die **fopen_s** -Funktion öffnet die Datei, die durch *filename*angegeben wird. **_wfopen_s** ist eine breit Zeichen Version von **fopen_s**. die Argumente für **_wfopen_s** sind Zeichen folgen mit breit Zeichen. **_wfopen_s** und **fopen_s** Verhalten sich andernfalls identisch.

**fopen_s** akzeptiert Pfade, die zum Zeitpunkt der Ausführung im Dateisystem gültig sind. UNC-Pfade und Pfade mit zugeordneten Netzlaufwerken werden von **fopen_s** akzeptiert, solange das System, das den Code ausführt, zum Zeitpunkt der Ausführung Zugriff auf die Freigabe oder das zugeordnete Netzlaufwerk hat. Wenn Sie Pfade für **fopen_s**erstellen, nehmen Sie keine Annahmen über die Verfügbarkeit von Laufwerken, Pfaden oder Netzwerkfreigaben in der Ausführungsumgebung vor. Als Verzeichnistrennzeichen in einem Pfad können Sie entweder den Schrägstrich (/) oder den umgekehrten Schrägstrich (\\) verwenden.

Diese Funktionen überprüfen ihre Parameter. Wenn *Pfile*, *filename*oder *Mode* ein NULL-Zeiger ist, generieren diese Funktionen eine Ausnahme wegen eines ungültigen Parameters, wie in [Parameter Validation (Parameter](../../c-runtime-library/parameter-validation.md)Überprüfung) beschrieben.

Überprüfen Sie stets den Rückgabewert, um festzustellen, ob die Funktion erfolgreich war, bevor Sie mit der Datei andere Vorgänge ausführen. Wenn ein Fehler auftritt, wird der Fehlercode zurückgegeben, und die globale Variable **errno** wird festgelegt. Weitere Informationen finden Sie unter [errno, _doserrno, _sys_errlist und _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen hierzu finden Sie unter [globaler Status in der CRT](../global-state.md).

## <a name="unicode-support"></a>Unicode-Unterstützung

**fopen_s** unterstützt Unicode-Dateistreams. Um eine neue oder vorhandene Unicode-Datei zu öffnen, übergeben Sie ein *CCS* -Flag, das die gewünschte Codierung angibt, an **fopen_s**:

**fopen_s (&FP, "newFile. txt", "RW, CCS =**_Encoding_**");**

Zulässige *Codierungs* Werte sind **Unicode**, **UTF-8**und **UTF-16LE**. Wenn kein Wert für die *Codierung*angegeben ist, **fopen_s** die ANSI-Codierung verwendet.

Wenn die Datei bereits vorhanden ist und zum Lesen oder Anhängen geöffnet ist, bestimmt die Bytereihenfolge-Marke (BOM), sofern in der Datei vorhanden, die Codierung. Die BOM-Codierung hat Vorrang vor der durch das *CCS* -Flag angegebenen Codierung. Die *CCS* -Codierung wird nur verwendet, wenn keine BOM vorhanden ist oder wenn es sich um eine neue Datei handelt.

> [!NOTE]
> Die BOM-Erkennung gilt nur für Dateien, die im Unicode-Modus geöffnet werden. Das heißt, indem das *CCS* -Flag übergeben wird.

In der folgenden Tabelle werden die Modi für verschiedene *CCS* -Flags zusammengefasst, die **fopen_s** und für Byte Reihenfolge Marken in der Datei angegeben werden.

### <a name="encodings-used-based-on-ccs-flag-and-bom"></a>Verwendete Codierungen auf Grundlage von ccs-Flag und BOM

|CCS-Flag|Keine BOM (oder neue Datei)|BOM: UTF-8|BOM: UTF-16|
|----------------|----------------------------|-----------------|------------------|
|**UNICODE**|**UTF-16LE**|**UTF-8**|**UTF-16LE**|
|**UTF-8**|**UTF-8**|**UTF-8**|**UTF-16LE**|
|**UTF-16LE**|**UTF-16LE**|**UTF-8**|**UTF-16LE**|

In Dateien, die zum Schreiben im Unicode-Modus geöffnet werden, wird automatisch eine BOM geschrieben.

Wenn *mode* der Modus **"a, CCS =**_Encoding_**"** ist, versucht **fopen_s** zuerst, die Datei mit Lesezugriff und Schreibzugriff zu öffnen. Ist der Vorgang erfolgreich, liest die Funktion die BOM, um die Codierung für die Datei zu bestimmen. Schlägt der Vorgang fehl, verwendet die Funktion die Standardcodierung für die Datei. In beiden Fällen öffnet **fopen_s** die Datei erneut mit Schreib geschütztem Zugriff. (Dies gilt nur für **einen** Modus, nicht für **ein +**.)

### <a name="generic-text-routine-mappings"></a>Zuordnung generischer Textroutinen

|TCHAR.H-Routine|_UNICODE und _MBCS nicht definiert.|_MBCS definiert|_UNICODE definiert|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tfopen_s**|**fopen_s**|**fopen_s**|**_wfopen_s**|

Der Zeichen folgen *Modus* gibt die Art des Zugriffs, der für die Datei angefordert wird, wie folgt an.

|*mode*|Zugriff|
|-|-|
| **r** | Öffnet zum Lesen. Wenn die Datei nicht vorhanden ist oder nicht gefunden werden kann, tritt beim **fopen_s** -Befehl ein Fehler auf. |
| **Löw** | Öffnet eine leere Datei zum Schreiben. Wenn die angegebene Datei vorhanden ist, wird ihr Inhalt zerstört. |
| **ein** | Wird vor dem Schreiben neuer Daten in die Datei zum Schreiben am Ende der Datei (Anfügen) geöffnet, ohne die EOF-Markierung (end-of-file, Dateiende) zu entfernen. Erstellt die Datei, wenn sie nicht vorhanden ist. |
| **"r +"** | Öffnet sowohl zum Lesen als auch zum Schreiben. Die Datei muss vorhanden sein. |
| **"w +"** | Öffnet eine leere Datei zum Lesen und Schreiben. Wenn die Datei vorhanden ist, wird ihr Inhalt zerstört. |
| **"a +"** | Öffnet sich zum Lesen und Anfügen. Der Anfügevorgang umfasst das Entfernen der EOF-Markierung, bevor neue Daten in die Datei geschrieben werden. Die EOF-Markierung wird nach Abschluss des Schreibvorgangs nicht wiederhergestellt. Erstellt die Datei, wenn sie nicht vorhanden ist. |

Wenn eine Datei mit dem Zugriffstyp **"a"** oder **"a +"** geöffnet wird, erfolgen alle Schreibvorgänge am Ende der Datei. Der Dateizeiger kann mithilfe von [fseek](fseek-fseeki64.md) oder [Rewind](rewind.md)neu positioniert werden. er wird jedoch immer wieder zurück an das Ende der Datei verschoben, bevor ein Schreibvorgang durchgeführt wird, damit vorhandene Daten nicht überschrieben werden können.

Der **"a"** -Modus entfernt die EOF-Markierung nicht, bevor Sie an die Datei angehängt wird. Nach dem Anfügen werden durch den MS-DOS-Befehl TYPE nur Daten bis zur ursprünglichen EOF-Markierung angezeigt, aber keine Daten, die an die Datei angefügt wurden. Der **"+"** -Modus entfernt die EOF-Markierung, bevor Sie an die Datei angehängt wird. Nach dem Anhängen werden mit dem Befehl MS-DOS TYPE alle Daten in der Datei angezeigt. Der Modus **"a +"** ist zum Anfügen an eine streamdatei erforderlich, die mit der EOF-Markierung STRG + Z beendet wird.

Wenn der Zugriffstyp **"r +"**, **"w +"** oder **"a +** " angegeben wird, sind sowohl Lese-als auch Schreibvorgänge zulässig. (Die Datei wird als "Update" geöffnet.) Wenn Sie jedoch vom Lesevorgang in den Schreibvorgang wechseln, muss für den Eingabevorgang ein EOF-Marker angezeigt werden. Wenn keine EOF-Markierung vorhanden ist, müssen Sie einen zwischenzeitlichen Aufruf einer dateipositionierenden Funktion verwenden. Die Funktionen für die Datei Positionierung sind " **f**", " [f Seek](fseek-fseeki64.md)" und " [Rewind](rewind.md)". Wenn Sie vom Schreibvorgang in den Lesevorgang wechseln, müssen **Sie entweder einen** zwischenzeitlichen oder einen zwischenzeitlichen aufzurufenden oder zu einer Datei positionierenden Funktion verwenden.

Zusätzlich zu den obigen Werten können die folgenden Zeichen im- *Modus* enthalten sein, um den Übersetzungsmodus für Zeilen Umleitungs Zeichen anzugeben:

|*mode* modusmodifizierer|Übersetzungsmodus|
|-|-|
| **Bund** | Öffnen im Textmodus (übersetzt). |
| **b** | Im binären (nicht übersetzten) Modus öffnen; Übersetzungen mit Wagen Rücklauf-und Zeilenvorschub Zeichen werden unterdrückt. |

Im Text Modus (übersetzt) wird STRG + Z bei der Eingabe als Dateiendezeichen interpretiert. In Dateien, die für das Lesen/Schreiben mit **"a +"** geöffnet sind, prüft **fopen_s** am Ende der Datei auf STRG + Z und entfernt es, wenn möglich. Dies geschieht, da die Verwendung von [fseek](fseek-fseeki64.md) und **ftell** zum Verschieben innerhalb einer Datei, die mit STRG + Z endet, dazu führen kann, dass sich [fseek](fseek-fseeki64.md) in der Nähe des Datei Endes nicht ordnungsgemäß verhält.

Im Textmodus werden Wagen Rücklauf-/Zeilenvorschub-Kombinationen bei Eingaben in einzeilige Feeds übersetzt, und Zeilenvorschub Zeichen werden bei der Ausgabe in Wagen Rücklauf-Zeilenvorschub-Kombinationen übersetzt. Wenn eine Stream-E/A-Funktion von Unicode im Textmodus (Standard) funktioniert, wird angenommen, dass es sich bei Quell- oder Zielstream um eine Sequenz von Multibytezeichen handelt. Daher konvertieren die Unicode-Streameingabefunktionen Multibytezeichen in Breitzeichen (wie bei einem Aufruf der **mbtowc**-Funktion). Aus demselben Grund konvertieren die Unicode-Streamausgabefunktionen Breitzeichen in Multibytezeichen (wie bei einem Aufruf der **wctomb**-Funktion).

Wenn " **t** " oder " **b** " im- *Modus*nicht angegeben wird, wird der Standard Übersetzungsmodus durch die globale Variable [_fmode](../../c-runtime-library/fmode.md)definiert. Wenn **t** oder **b** dem Argument vorangestellt wird, schlägt die Funktion fehl und gibt **null**zurück.

Weitere Informationen zur Anwendung von Text- und Binärmodi in Unicode- und Multibyte-Stream-E/A finden Sie unter [Text- und Binärmodus-Datei-E/A](../../c-runtime-library/text-and-binary-mode-file-i-o.md) und [Unicode-Stream-E/A in Text- und Binärmodi](../../c-runtime-library/unicode-stream-i-o-in-text-and-binary-modes.md).

|*mode* modusmodifizierer|Verhalten|
|-|-|
| **scher** | Aktivieren Sie das commitflag für den zugeordneten *Dateinamen* , damit der Inhalt des Datei Puffers direkt auf den Datenträger geschrieben wird, wenn entweder **fflush** oder **_flushall** aufgerufen wird. |
| **n** | Setzen Sie das commitflag für den zugeordneten *Dateinamen* auf "No-Commit" zurück. Dies ist die Standardeinstellung. Dabei wird auch das globale Commitflag überschrieben, wenn Sie das Programm mit COMMODE.OBJ verknüpfen. Der Standardwert des globalen Commitflags lautet "no-commit", es sei denn, Sie verknüpfen das Programm explizit mit COMMODE.OBJ (siehe [Link Options](../../c-runtime-library/link-options.md)). |
| **N** | Gibt an, dass die Datei nicht von untergeordneten Prozessen geerbt wird. |
| **E** | Gibt an, dass das Zwischenspeichern für den sequenziellen Zugriff vom Datenträger optimiert, aber nicht darauf beschränkt ist. |
| **R** | Gibt an, dass das Zwischenspeichern für den zufälligen Zugriff vom Datenträger optimiert, aber nicht darauf beschränkt ist. |
| **T** | Gibt an, dass eine Datei temporär ist. Wenn möglich, wird sie nicht auf den Datenträger geschrieben. |
| **D** | Gibt an, dass eine Datei temporär ist. Sie wird gelöscht, wenn der letzte Dateizeiger geschlossen wird. |
| **CCS =**_Codierung_ | Gibt den codierten Zeichensatz an, der für diese Datei verwendet werden soll (einer der **UTF-8**, **UTF-16LE**oder **Unicode**). Machen Sie keine Angabe, wenn Sie ANSI-Codierung wünschen. |

Gültige Zeichen *für die im* **fopen_s** und [_fdopen](fdopen-wfdopen.md) verwendete moduszeichenfolge entsprechen *Oflag* -Argumenten, die wie folgt in [_open](open-wopen.md) und [_sopen](sopen-wsopen.md)verwendet werden.

|Zeichen in der *Mode* -Zeichenfolge|Entsprechender *Oflag* -Wert für _open/_sopen|
|-------------------------------|----------------------------------------------------|
|**ein**|**_O_WRONLY** &#124; **_O_APPEND** (in der Regel **_O_WRONLY** **&#124; _O_CREAT &#124;** **_O_APPEND**)|
|**a +**|**_O_RDWR** &#124; **_O_APPEND** (in der Regel **_O_RDWR** **&#124; _O_APPEND &#124;** **_O_CREAT**)|
|**r**|**_O_RDONLY**|
|**r +**|**_O_RDWR**|
|**w**|**_O_WRONLY** (in der Regel **_O_WRONLY** &#124; **_O_CREAT** **&#124;)**|
|**w +**|**_O_RDWR** (in der Regel **_O_RDWR** &#124; **_O_CREAT** **&#124;)**|
|**b**|**_O_BINARY**|
|**Bund**|**_O_TEXT**|
|**scher**|Keine|
|**n**|Keine|
|**E**|**_O_SEQUENTIAL**|
|**R**|**_O_RANDOM**|
|**T**|**_O_SHORTLIVED**|
|**D**|**_O_TEMPORARY**|
|**CCS = Unicode**|**_O_WTEXT**|
|**CCS = UTF-8**|**_O_UTF8**|
|**CCS = UTF-16LE**|**_O_UTF16**|

Wenn Sie den **RB** -Modus verwenden, den Code nicht portieren müssen und davon ausgehen, dass ein Großteil der Datei gelesen wird und/oder die Netzwerkleistung nicht relevant ist, können Win32-Dateien mit Speicher Zuordnung auch eine Option sein.

## <a name="requirements"></a>Requirements (Anforderungen)

|Funktion|Erforderlicher Header|
|--------------|---------------------|
|**fopen_s**|\<stdio.h>|
|**_wfopen_s**|\<stdio.h> oder \<wchar.h>|

Zusätzliche Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Bibliotheken

Alle Versionen [C-Laufzeitbibliotheken](../../c-runtime-library/crt-library-features.md).

Die Optionen **c**, **n**und **t** *mode* sind Microsoft-Erweiterungen für **fopen_s** und [_fdopen](fdopen-wfdopen.md) und sollten nicht verwendet werden, wenn ANSI-Portabilität gewünscht wird.

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

## <a name="see-also"></a>Weitere Informationen

[Stream-E/A](../../c-runtime-library/stream-i-o.md)<br/>
[fclose, _fcloseall](fclose-fcloseall.md)<br/>
[_fdopen, _wfdopen](fdopen-wfdopen.md)<br/>
[ferror](ferror.md)<br/>
[_fileno](fileno.md)<br/>
[freopen, _wfreopen](freopen-wfreopen.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
[_setmode](setmode.md)<br/>
