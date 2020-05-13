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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: 7c7f079d8867416ab4f091d7c95a01ab9e40c0e8
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/07/2020
ms.locfileid: "82910156"
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

*Einfügen*<br/>
Name der zu öffnenden Datei.

*mode*<br/>
Zugriffstyp zulässig.

*shflag*<br/>
Freigabetyp erlaubt.

## <a name="return-value"></a>Rückgabewert

Jede dieser Funktionen gibt einen Zeiger auf den Stream zurück. Ein NULL-Zeigerwert gibt einen Fehler an. Wenn *filename* oder *Mode* **null** oder eine leere Zeichenfolge ist, rufen diese Funktionen den Handler für ungültige Parameter auf, wie in [Parameter Validation (Parameter](../../c-runtime-library/parameter-validation.md)Überprüfung) beschrieben. Wenn die weitere Ausführung zugelassen wird, geben diese Funktionen **null** zurück und legen **errno** auf **EINVAL**fest.

Weitere Informationen zu diesen und anderen Fehlercodes finden Sie unter [_doserrno, errno, _sys_errlist und _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Hinweise

Die **_fsopen** -Funktion öffnet die Datei, die durch *filename* angegeben ist, als Datenstrom und bereitet die Datei auf nachfolgende freigegebene Lese-oder Schreibvorgänge vor, wie im Modus-und *shflag* -Argument definiert. **_wfsopen** ist eine breit Zeichen Version von **_fsopen**. der *Dateiname* und die *Modusargumente für* **_wfsopen** sind Zeichen folgen mit breit Zeichen. **_wfsopen** und **_fsopen** Verhalten sich andernfalls identisch.

Der Zeichen folgen *Modus* gibt den für die Datei angeforderten Zugriffstyp an, wie in der folgenden Tabelle dargestellt.

|Begriff|Definition|
|----------|----------------|
|**r**|Öffnet zum Lesen. Wenn die Datei nicht vorhanden ist oder nicht gefunden werden kann, tritt beim **_fsopen** -Befehl ein Fehler auf.|
|**Löw**|Öffnet eine leere Datei zum Schreiben. Wenn die angegebene Datei vorhanden ist, wird ihr Inhalt zerstört.|
|**ein**|Öffnet zum Schreiben am Ende der Datei (Anfügen); erstellt die Datei zuerst, wenn sie nicht vorhanden ist.|
|**"r +"**|Öffnet sowohl zum Lesen als auch zum Schreiben. (Die Datei muss vorhanden sein.)|
|**"w +"**|Öffnet eine leere Datei zum Lesen und Schreiben. Wenn die angegebene Datei vorhanden ist, wird ihr Inhalt zerstört.|
|**"a +"**|Öffnet zum Lesen und Anhängen; erstellt die Datei zuerst, wenn sie nicht vorhanden ist.|

Verwenden Sie die Typen **"w"** und **"w +"** mit Sorgfalt, da Sie vorhandene Dateien zerstören können.

Wenn eine Datei mit dem Zugriffstyp **"a"** oder **"a +"** geöffnet wird, erfolgen alle Schreibvorgänge am Ende der Datei. Der Dateizeiger kann mithilfe von [fseek](fseek-fseeki64.md) oder [Rewind](rewind.md)neu positioniert werden. er wird jedoch immer wieder zurück an das Ende der Datei verschoben, bevor ein Schreibvorgang durchgeführt wird. Folglich können vorhandene Daten nicht überschrieben werden. Wenn der Zugriffstyp **"r +"**, **"w +"** oder **"a +** " angegeben wird, sind sowohl Lese-als auch Schreibvorgänge zulässig (die Datei ist zum Aktualisieren geöffnet). Wenn Sie jedoch zwischen Lesen und Schreiben wechseln, muss ein sich dazwischen befindender Vorgang wie [fsetpos](fsetpos.md), [fseek](fseek-fseeki64.md) oder [rewind](rewind.md) vorhanden sein. Wenn gewünscht, kann die aktuelle Position für den Vorgang " [f](fsetpos.md) " oder " [f](fseek-fseeki64.md) " angegeben werden. Zusätzlich zu den oben aufgeführten Werten kann eines der folgenden Zeichen in den- *Modus* eingeschlossen werden, um den Übersetzungsmodus für neue Zeilen anzugeben, und für die Dateiverwaltung.

|Begriff|Definition|
|----------|----------------|
|**Bund**|Öffnet eine Datei im Textmodus (übersetzt). In diesem Modus werden Wagen Rücklauf-Zeilenvorschub-Kombinationen (CR-LF) bei der Eingabe in einzeilige Feeds (LF) übersetzt. LF-Zeichen werden bei der Ausgabe in CR-LF-Kombinationen übersetzt. Außerdem wird STRG+Z bei der Eingabe als EOF-Zeichen interpretiert. In Dateien, die für Lese-oder Lese-/Schreibzugriff geöffnet sind, überprüft **_fsopen** , ob am Ende der Datei STRG + Z angezeigt wird, und entfernt, wenn möglich. Dies geschieht, da die Verwendung von [fseek](fseek-fseeki64.md) und [ftell](ftell-ftelli64.md) zum Verschieben innerhalb einer Datei, die mit STRG + Z endet, dazu führen kann, dass sich [fseek](fseek-fseeki64.md) in der Nähe des Datei Endes nicht ordnungsgemäß verhält.|
|**b**|Öffnet im (unübersetzten) Binärmodus eine Datei; die oben genannten Übersetzungen werden unterdrückt.|
|**Hymnen**|Gibt an, dass das Zwischenspeichern für den sequenziellen Zugriff vom Datenträger optimiert, aber nicht darauf beschränkt ist.|
|**R**|Gibt an, dass das Zwischenspeichern für den zufälligen Zugriff vom Datenträger optimiert, aber nicht darauf beschränkt ist.|
|**T**|Gibt an, dass eine Datei temporär ist. Wenn möglich, wird sie nicht auf den Datenträger geschrieben.|
|**D**|Gibt an, dass eine Datei temporär ist. Sie wird gelöscht, wenn der letzte Dateizeiger geschlossen wird.|

Wenn **t** oder **b** nicht in *mode* angegeben ist, wird der Übersetzungsmodus durch die Standardmodusvariable **_fmode** definiert. Wenn **t** oder **b** dem Argument vorangestellt wird, schlägt die Funktion fehl und gibt **null**zurück. Eine Erörterung von Text- und Binärmodi finden Sie unter [Text- und Binärmodusdatei-E/A](../../c-runtime-library/text-and-binary-mode-file-i-o.md).

Das Argument *shflag* ist ein konstanter Ausdruck, der aus einer der folgenden Manifest-Konstanten besteht, die in "Share. h" definiert sind.

|Begriff|Definition|
|----------|----------------|
|**_SH_COMPAT**|Legt den Kompatibilitätsmodus für 16-Bit-Anwendungen fest.|
|**_SH_DENYNO**|Erlaubt Lese- und Schreibzugriff.|
|**_SH_DENYRD**|Verweigert den Lesezugriff auf die Datei.|
|**_SH_DENYRW**|Verweigert den Lese- und Schreibzugriff auf die Datei.|
|**_SH_DENYWR**|Verweigert den Lesezugriff auf die Datei.|

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen hierzu finden Sie unter [globaler Status in der CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Zuordnung generischer Textroutinen

|Tchar.h-Routine|_UNICODE und _MBCS nicht definiert|_MBCS definiert|_UNICODE definiert|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tfsopen**|**_fsopen**|**_fsopen**|**_wfsopen**|

## <a name="requirements"></a>Anforderungen

|Funktion|Erforderlicher Header|Optionale Header|
|--------------|---------------------|----------------------|
|**_fsopen**|\<stdio.h>|\<share.h><br /><br /> Für die Manifest-Konstante für den *shflag* -Parameter.|
|**_wfsopen**|\<stdio.h> oder \<wchar.h>|\<share.h><br /><br /> Für die Manifest-Konstante für den *shflag* -Parameter.|

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

## <a name="see-also"></a>Weitere Informationen

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
