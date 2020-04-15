---
title: _fsopen, _wfsopen
ms.date: 4/2/2020
api_name:
- _wfsopen
- _fsopen
- _o__fsopen
- _o__wfsopen
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
- wfsopen
- fsopen
- tfsopen
- _tfsopen
- _wfsopen
- _fsopen
helpviewer_keywords:
- opening files, streams
- fsopen function
- tfsopen function
- wfsopen function
- _fsopen function
- files [C++], opening
- _tfsopen function
- _wfsopen function
- file sharing [C++]
ms.assetid: 5e4502ab-48a9-4bee-a263-ebac8d638dec
ms.openlocfilehash: 49907808729375e3bea18a5f4bbf204852e0072a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81345702"
---
# <a name="_fsopen-_wfsopen"></a>_fsopen, _wfsopen

Ein Stream mit Dateifreigabe öffnen

## <a name="syntax"></a>Syntax

```C
FILE *_fsopen(
   const char *filename,
   const char *mode,
   int shflag
);
FILE *_wfsopen(
   const wchar_t *filename,
   const wchar_t *mode,
   int shflag
);
```

### <a name="parameters"></a>Parameter

*Dateiname*<br/>
Name der zu öffnenden Datei.

*Modus*<br/>
Zugriffstyp zulässig.

*shflag*<br/>
Freigabetyp erlaubt.

## <a name="return-value"></a>Rückgabewert

Jede dieser Funktionen gibt einen Zeiger auf den Stream zurück. Ein NULL-Zeigerwert gibt einen Fehler an. Wenn *Dateiname* oder *Modus* **NULL** oder eine leere Zeichenfolge ist, rufen diese Funktionen den ungültigen Parameterhandler auf, wie unter [Parametervalidierung](../../c-runtime-library/parameter-validation.md)beschrieben. Wenn die Ausführung fortgesetzt werden darf, geben diese Funktionen **NULL** zurück und setzen **errno** auf **EINVAL**.

Weitere Informationen zu diesen und anderen Fehlercodes finden Sie unter [_doserrno, errno, _sys_errlist und _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Bemerkungen

Die **_fsopen-Funktion** öffnet die datei, die durch *filename* als Stream angegeben wird, und bereitet die Datei auf das nachfolgende gemeinsame Lesen oder Schreiben vor, wie durch die Argumente mode und *shflag* definiert. **_wfsopen** ist eine breit **gefächerte**Version von _fsopen ; Die **Zu-** und _wfsopen *Dateinamen-* und *Modusargumente* sind Zeichenfolgen mit großen Zeichen. **_wfsopen** und **_fsopen** verhalten sich ansonsten gleich.

Der *Zeichenkettenmodus* gibt den Typ des für die Datei angeforderten Zugriffs an, wie in der folgenden Tabelle dargestellt.

|Begriff|Definition|
|----------|----------------|
|**"r"**|Öffnet zum Lesen. Wenn die Datei nicht vorhanden ist oder nicht gefunden werden kann, schlägt der **_fsopen-Aufruf** fehl.|
|**"w"**|Öffnet eine leere Datei zum Schreiben. Wenn die angegebene Datei vorhanden ist, wird ihr Inhalt zerstört.|
|**"a"**|Öffnet zum Schreiben am Ende der Datei (Anfügen); erstellt die Datei zuerst, wenn sie nicht vorhanden ist.|
|**"r+"**|Öffnet sowohl zum Lesen als auch zum Schreiben. (Die Datei muss vorhanden sein.)|
|**"w+"**|Öffnet eine leere Datei zum Lesen und Schreiben. Wenn die angegebene Datei vorhanden ist, wird ihr Inhalt zerstört.|
|**"a+"**|Öffnet zum Lesen und Anhängen; erstellt die Datei zuerst, wenn sie nicht vorhanden ist.|

Verwenden Sie die Typen **"w"** und **"w+"** mit Vorsicht, da sie vorhandene Dateien zerstören können.

Wenn eine Datei mit dem Zugriffstyp **"a"** oder **"a+"** geöffnet wird, werden alle Schreibvorgänge am Ende der Datei ausgeführt. Der Dateizeiger kann mit [fseek](fseek-fseeki64.md) oder [reswind](rewind.md)neu positioniert werden, aber er wird immer wieder an das Ende der Datei verschoben, bevor ein Schreibvorgang ausgeführt wird. Daher können vorhandene Daten nicht überschrieben werden. Wenn der Zugriffstyp **"r+"**, **"w+"** oder **"a+"** angegeben ist, sind sowohl Lesen als auch Schreiben zulässig (die Datei soll für die Aktualisierung geöffnet sein). Wenn Sie jedoch zwischen Lesen und Schreiben wechseln, muss ein sich dazwischen befindender Vorgang wie [fsetpos](fsetpos.md), [fseek](fseek-fseeki64.md) oder [rewind](rewind.md) vorhanden sein. Die aktuelle Position kann bei Bedarf für den [Fsetpos-](fsetpos.md) oder [fseek-Vorgang](fseek-fseeki64.md) angegeben werden. Zusätzlich zu den oben genannten Werten kann eines der folgenden Zeichen in den *Modus* einbezogen werden, um den Übersetzungsmodus für neue Zeilen und für die Dateiverwaltung anzugeben.

|Begriff|Definition|
|----------|----------------|
|**T**|Öffnet eine Datei im Textmodus (übersetzt). In diesem Modus werden Wagenrücklaufkombinationen (CR-LF) bei Eingaben in Einzeilenvorschübe (LF) und LF-Zeichen am Ausgang in CR-LF-Kombinationen übersetzt. Außerdem wird STRG+Z bei der Eingabe als EOF-Zeichen interpretiert. In Dateien, die zum Lesen oder Lesen/Schreiben geöffnet werden, **sucht _fsopen** nach einem STRG+Z am Ende der Datei und entfernt sie, wenn möglich. Dies geschieht, weil die Verwendung von [fseek](fseek-fseeki64.md) und [ftell](ftell-ftelli64.md) zum Verschieben innerhalb einer Datei, die mit einer STRG+Z endet, dazu führen kann, dass [fseek](fseek-fseeki64.md) sich am Ende der Datei falsch verhält.|
|**B**|Öffnet im (unübersetzten) Binärmodus eine Datei; die oben genannten Übersetzungen werden unterdrückt.|
|**E**|Gibt an, dass das Zwischenspeichern für den sequenziellen Zugriff vom Datenträger optimiert, aber nicht darauf beschränkt ist.|
|**R**|Gibt an, dass das Zwischenspeichern für den zufälligen Zugriff vom Datenträger optimiert, aber nicht darauf beschränkt ist.|
|**T**|Gibt an, dass eine Datei temporär ist. Wenn möglich, wird sie nicht auf den Datenträger geschrieben.|
|**D**|Gibt an, dass eine Datei temporär ist. Sie wird gelöscht, wenn der letzte Dateizeiger geschlossen wird.|

Wenn **t** oder **b** nicht in *mode* angegeben ist, wird der Übersetzungsmodus durch die Standardmodusvariable **_fmode** definiert. Wenn dem Argument **t** oder **b** der Vorzeichen vorangestellt ist, schlägt die Funktion fehl und gibt **NULL**zurück. Eine Erörterung von Text- und Binärmodi finden Sie unter [Text- und Binärmodusdatei-E/A](../../c-runtime-library/text-and-binary-mode-file-i-o.md).

Das Argument *shflag* ist ein konstanter Ausdruck, der aus einer der folgenden Manifestkonstanten besteht, die in Share.h definiert sind.

|Begriff|Definition|
|----------|----------------|
|**_SH_COMPAT**|Legt den Kompatibilitätsmodus für 16-Bit-Anwendungen fest.|
|**_SH_DENYNO**|Erlaubt Lese- und Schreibzugriff.|
|**_SH_DENYRD**|Verweigert den Lesezugriff auf die Datei.|
|**_SH_DENYRW**|Verweigert den Lese- und Schreibzugriff auf die Datei.|
|**_SH_DENYWR**|Verweigert den Lesezugriff auf die Datei.|

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen dazu finden Sie [unter Globaler Status in der CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Zuordnung generischer Textroutinen

|Tchar.h-Routine|_UNICODE und _MBCS nicht definiert|_MBCS definiert|_UNICODE definiert|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tfsopen**|**_fsopen**|**_fsopen**|**_wfsopen**|

## <a name="requirements"></a>Anforderungen

|Funktion|Erforderlicher Header|Optionale Header|
|--------------|---------------------|----------------------|
|**_fsopen**|\<stdio.h>|\<share.h><br /><br /> Für Manifestkonstante für *shflag-Parameter.*|
|**_wfsopen**|\<stdio.h> oder \<wchar.h>|\<share.h><br /><br /> Für Manifestkonstante für *shflag-Parameter.*|

## <a name="example"></a>Beispiel

```C
// crt_fsopen.c

#include <stdio.h>
#include <stdlib.h>
#include <share.h>

int main( void )
{
   FILE *stream;

   // Open output file for writing. Using _fsopen allows us to
   // ensure that no one else writes to the file while we are
   // writing to it.
    //
   if( (stream = _fsopen( "outfile", "wt", _SH_DENYWR )) != NULL )
   {
      fprintf( stream, "No one else in the network can write "
                       "to this file until we are done.\n" );
      fclose( stream );
   }
   // Now others can write to the file while we read it.
   system( "type outfile" );
}
```

```Output
No one else in the network can write to this file until we are done.
```

## <a name="see-also"></a>Siehe auch

[Stream-E/A](../../c-runtime-library/stream-i-o.md)<br/>
[fclose, _fcloseall](fclose-fcloseall.md)<br/>
[_fdopen, _wfdopen](fdopen-wfdopen.md)<br/>
[ferror](ferror.md)<br/>
[_fileno](fileno.md)<br/>
[fopen, _wfopen](fopen-wfopen.md)<br/>
[freopen, _wfreopen](freopen-wfreopen.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
[_setmode](setmode.md)<br/>
[_sopen, _wsopen](sopen-wsopen.md)<br/>
