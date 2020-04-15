---
title: freopen_s, _wfreopen_s
ms.date: 4/2/2020
api_name:
- _wfreopen_s
- freopen_s
- _o__wfreopen_s
- _o_freopen_s
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
- freopen_s
- _tfreopen_s
- _wfreopen_s
helpviewer_keywords:
- _tfreopen_s function
- _wfreopen_s function
- file pointers [C++], reassigning
- tfreopen_s function
- wfreopen_s function
- freopen_s function
ms.assetid: ad25a4da-6ad4-476b-a86d-660b221ca84d
ms.openlocfilehash: a24e34ead905d2f704bfbf4d829064c656272e97
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81345915"
---
# <a name="freopen_s-_wfreopen_s"></a>freopen_s, _wfreopen_s

Weist einen Dateizeiger neu zu. Diese Versionen von [freopen, _wfreopen](freopen-wfreopen.md) enthalten Sicherheitserweiterungen, wie unter [Sicherheitsfunktionen in der CRT](../../c-runtime-library/security-features-in-the-crt.md) beschrieben.

## <a name="syntax"></a>Syntax

```C
errno_t freopen(
   FILE** pFile,
   const char *path,
   const char *mode,
   FILE *stream
);
errno_t _wfreopen(
   FILE** pFile,
   const wchar_t *path,
   const wchar_t *mode,
   FILE *stream
);
```

### <a name="parameters"></a>Parameter

*pFile*<br/>
Ein Zeiger auf den vom Aufruf bereitzustellenden Dateizeiger.

*path*<br/>
Pfad der neuen Datei.

*Modus*<br/>
Zugriffstyp zulässig.

*Stream*<br/>
Zeiger auf die **FILE**-Struktur.

## <a name="return-value"></a>Rückgabewert

Jede dieser Funktionen gibt einen Fehlercode zurück. Wenn ein Fehler auftritt, wird die ursprüngliche Datei geschlossen.

## <a name="remarks"></a>Bemerkungen

Die **freopen_s-Funktion** schließt die Datei, die derzeit dem *Stream* zugeordnet ist, und weist der datei, die durch *pfad*angegeben wird, den *Stream* neu zu. **_wfreopen_s** ist eine breit **gefächerte**Version von _freopen_s ; Die *Pfad-* und *Modusargumente* für **_wfreopen_s** sind Zeichenfolgen mit großen Zeichen. **_wfreopen_s** und **_freopen_s** verhalten sich ansonsten gleich.

Wenn *pFile*, *path*, *mode*oder *stream* **NULL**sind oder wenn *path* eine leere Zeichenfolge ist, rufen diese Funktionen den ungültigen Parameterhandler auf, wie unter [Parametervalidierung](../../c-runtime-library/parameter-validation.md)beschrieben. Wenn die Ausführung fortgesetzt werden darf, setzen diese Funktionen **errno** auf **EINVAL** und geben **EINVAL**zurück.

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen dazu finden Sie [unter Globaler Status in der CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Zuordnung generischer Textroutinen

|TCHAR.H-Routine|_UNICODE und _MBCS nicht definiert.|_MBCS definiert|_UNICODE definiert|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tfreopen_s**|**freopen_s**|**freopen_s**|**_wfreopen_s**|

**freopen_s** wird in der Regel verwendet, um die vorgeöffneten Dateien **stdin**, **stdout**und **stderr** in Dateien, die vom Benutzer angegeben umgeleitet werden. Die neue Datei, die dem *Stream* zugeordnet ist, wird mit *mode*geöffnet, d. a. der Zeichenkette, die den für die Datei angeforderten Zugriffstyp angibt:

|*Modus*|Zugriff|
|-|-|
| **"r"** | Öffnet zum Lesen. Wenn die Datei nicht vorhanden ist oder nicht gefunden werden kann, schlägt der **freopen_s-Aufruf** fehl. |
| **"w"** | Öffnet eine leere Datei zum Schreiben. Wenn die angegebene Datei vorhanden ist, wird ihr Inhalt zerstört. |
| **"a"** | Wird vor dem Schreiben neuer Daten in die Datei zum Schreiben am Ende der Datei (Anfügen) geöffnet, ohne die EOF-Markierung (end-of-file, Dateiende) zu entfernen. Erstellt die Datei, wenn sie nicht vorhanden ist. |
| **"r+"** | Öffnet sowohl zum Lesen als auch zum Schreiben. Die Datei muss vorhanden sein. |
| **"w+"** | Öffnet eine leere Datei zum Lesen und Schreiben. Wenn die Datei vorhanden ist, wird ihr Inhalt zerstört. |
| **"a+"** | Öffnet sich zum Lesen und Anfügen. Der Anfügevorgang umfasst das Entfernen der EOF-Markierung, bevor neue Daten in die Datei geschrieben werden. Die EOF-Markierung wird nach Abschluss des Schreibvorgangs nicht wiederhergestellt. Erstellt die Datei, wenn sie nicht vorhanden ist. |

Verwenden Sie die Typen **"w"** und **"w+"** mit Vorsicht, da sie vorhandene Dateien zerstören können.

Wenn eine Datei mit dem Zugriffstyp **"a"** oder **"a+"** geöffnet wird, finden alle Schreibvorgänge am Ende der Datei statt. Obwohl der Dateizeiger mit [fseek](fseek-fseeki64.md) oder [reswind](rewind.md)neu positioniert werden kann, wird der Dateizeiger immer wieder an das Ende der Datei verschoben, bevor ein Schreibvorgang ausgeführt wird. Daher können vorhandene Daten nicht überschrieben werden.

Der **"a"-Modus** entfernt die EOF-Markierung nicht, bevor sie an die Datei angehängt wird. Nach dem Anfügen werden durch den MS-DOS-Befehl TYPE nur Daten bis zur ursprünglichen EOF-Markierung angezeigt, aber keine Daten, die an die Datei angefügt wurden. Der **Modus "a+"** entfernt die EOF-Markierung, bevor sie an die Datei angehängt wird. Nach dem Anhängen werden mit dem Befehl MS-DOS TYPE alle Daten in der Datei angezeigt. Der **Modus "a+"** ist zum Anfügen an eine Streamdatei erforderlich, die mit der STRG+Z-EOF-Markierung beendet wird.

Wenn der Zugriffstyp **"r+"**, **"w+"** oder **"a+"** angegeben ist, sind sowohl Lesen als auch Schreiben zulässig (die Datei soll für "update" geöffnet sein). Wenn Sie jedoch zwischen Lese- und Schreibvorgängen wechseln, muss ein sich dazwischen befindender Vorgang wie [fsetpos](fsetpos.md), [fseek](fseek-fseeki64.md) oder [rewind](rewind.md) vorhanden sein. Die aktuelle Position kann bei Bedarf für den [Fsetpos-](fsetpos.md) oder [fseek-Vorgang](fseek-fseeki64.md) angegeben werden. Zusätzlich zu den oben genannten Werten kann eines der folgenden Zeichen in die *Moduszeichenfolge* aufgenommen werden, um den Übersetzungsmodus für neue Zeilen anzugeben.

|*mode* Modusmodifizierer|Übersetzungsmodus|
|-|-|
| **T** | Öffnen im Textmodus (übersetzt). |
| **B** | Öffnen im binären (unübersetzten) Modus; Übersetzungen mit Wagen-Rücklauf- und Zeilenvorschubzeichen werden unterdrückt. |

Im Textmodus (übersetzt) werden die Kombinationen des Wagenrücklaufs (CR-LF) bei der Eingabe in Einzeilen-Feed-Zeichen (LF) übersetzt; LF-Zeichen werden bei der Ausgabe in CR-LF-Kombinationen übersetzt. Außerdem wird STRG+Z bei der Eingabe als EOF-Zeichen interpretiert. In Dateien, die zum Lesen oder zum Schreiben und Lesen mit **"a+"** geöffnet werden, sucht die Laufzeitbibliothek nach einem STRG+Z am Ende der Datei und entfernt sie, wenn möglich. Dies geschieht, weil die Verwendung von [fseek](fseek-fseeki64.md) und [ftell,](ftell-ftelli64.md) um innerhalb einer Datei zu verschieben, dazu führen kann, dass [fseek](fseek-fseeki64.md) sich am Ende der Datei falsch verhält. Die **option t** ist eine Microsoft-Erweiterung, die nicht verwendet werden sollte, wenn die ANSI-Portabilität gewünscht wird.

Wenn **t** oder **b** im *Modus*nicht angegeben ist, wird der Standard-Übersetzungsmodus durch die globale Variable [_fmode](../../c-runtime-library/fmode.md)definiert. Wenn dem Argument **t** oder **b** der Vorzeichen vorangestellt ist, schlägt die Funktion fehl und gibt **NULL**zurück.

Eine Erörterung von Text- und Binärmodi finden Sie unter [Text- und Binärmodusdatei-E/A](../../c-runtime-library/text-and-binary-mode-file-i-o.md).

## <a name="requirements"></a>Anforderungen

|Funktion|Erforderlicher Header|
|--------------|---------------------|
|**freopen_s**|\<stdio.h>|
|**_wfreopen_s**|\<stdio.h> oder \<wchar.h>|

Die Konsole wird in UWP-Apps (Universelle Windows-Plattform) nicht unterstützt. Die Standard-Stream-Handles, die der Konsole, **stdin**, **stdout**und **stderr**zugeordnet sind, müssen umgeleitet werden, bevor C-Laufzeitfunktionen sie in UWP-Apps verwenden können. Zusätzliche Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Beispiel

```C
// crt_freopen_s.c
// This program reassigns stderr to the file
// named FREOPEN.OUT and writes a line to that file.

#include <stdio.h>
#include <stdlib.h>

FILE *stream;

int main( void )
{
   errno_t err;
   // Reassign "stderr" to "freopen.out":
   err = freopen_s( &stream, "freopen.out", "w", stderr );

   if( err != 0 )
      fprintf( stdout, "error on freopen\n" );
   else
   {
      fprintf( stdout, "successfully reassigned\n" ); fflush( stdout );
      fprintf( stream, "This will go to the file 'freopen.out'\n" );
      fclose( stream );
   }
   system( "type freopen.out" );
}
```

```Output
successfully reassigned
This will go to the file 'freopen.out'
```

## <a name="see-also"></a>Siehe auch

[Stream-E/A](../../c-runtime-library/stream-i-o.md)<br/>
[freopen, _wfreopen](freopen-wfreopen.md)<br/>
[fclose, _fcloseall](fclose-fcloseall.md)<br/>
[_fdopen, _wfdopen](fdopen-wfdopen.md)<br/>
[_fileno](fileno.md)<br/>
[fopen, _wfopen](fopen-wfopen.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
[_setmode](setmode.md)<br/>
