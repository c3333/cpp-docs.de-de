---
title: _setmode
ms.date: 4/2/2020
api_name:
- _setmode
- _o__setmode
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
- _setmode
helpviewer_keywords:
- Unicode [C++], console output
- files [C++], modes
- _setmode function
- file translation [C++], setting mode
- files [C++], translation
- setmode function
ms.assetid: 996ff7cb-11d1-43f4-9810-f6097182642a
ms.openlocfilehash: abedba6f1d414191732859e3e44b54cc16acc4e9
ms.sourcegitcommit: 43cee7a0d41a062661229043c2f7cbc6ace17fa3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/13/2020
ms.locfileid: "92008421"
---
# <a name="_setmode"></a>_setmode

Legt den Dateiübersetzungsmodus fest.

## <a name="syntax"></a>Syntax

```C
int _setmode (
   int fd,
   int mode
);
```

### <a name="parameters"></a>Parameter

*FD*<br/>
Dateideskriptor.

*mode*<br/>
Neuer Übersetzungsmodus.

## <a name="return-value"></a>Rückgabewert

Im Erfolgsfall wird der vorherige Übersetzungsmodus zurückgegeben.

Wenn ungültige Parameter an die Funktion übergeben werden, wird der Handler für ungültige Parameter aufgerufen, wie in [Parameter Validation (Parameterüberprüfung)](../../c-runtime-library/parameter-validation.md)beschrieben. Wenn die weitere Ausführung zugelassen wird, gibt diese Funktion-1 zurück und legt **errno** entweder auf **EBADF**fest, das einen ungültigen Dateideskriptor angibt, oder auf **EINVAL**, das ein ungültiges Modusargument *angibt* .

Weitere Informationen zu diesen und anderen Rückgabecodes finden Sie unter [_doserrno, errno, _sys_errlist und _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Bemerkungen

Die **_setmode** -Funktion legt den *Modus* in den Übersetzungsmodus der von *FD*angegebenen Datei fest. Wenn Sie **_O_TEXT** as- *Modus* übergeben, wird der Modus Text (übersetzt) festgelegt. Die Kombinationen aus Wagen Rücklauf/Zeilenvorschub (CR-LF) werden bei der Eingabe in ein Einzel Zeilen-Feed-Zeichen übersetzt. Zeilenvorschubzeichen werden bei der Ausgabe in Kombinationen aus Wagenrücklauf und Zeilenvorschub (CR-LF) übersetzt. Durch übergeben **_O_BINARY** wird der binäre (nicht übersetzte) Modus festgelegt, in dem diese Übersetzungen unterdrückt werden.

Sie können auch **_O_U16TEXT**, **_O_U8TEXT**oder **_O_WTEXT** übergeben, um den Unicode-Modus zu aktivieren, wie im zweiten Beispiel weiter unten in diesem Dokument veranschaulicht.

> [!CAUTION]
> Der Unicode-Modus ist für breit Druckfunktionen (z. b. `wprintf` ) und wird für schmale Druckfunktionen nicht unterstützt. Die Verwendung einer schmalen Druckfunktion in einem Unicode-modusstream löst eine Assert-Funktion aus.

**_setmode** wird normalerweise verwendet, um den Standard Übersetzungsmodus von **stdin** und **stdout**zu ändern, aber Sie können Sie in jeder beliebigen Datei verwenden. Wenn Sie **_setmode** auf den Dateideskriptor für einen Stream anwenden, müssen Sie **_setmode** vor dem Ausführen von Eingabe-oder Ausgabe Vorgängen im Stream abrufen.

> [!CAUTION]
> Wenn Sie Daten in einen Dateistream schreiben, leeren Sie den Code explizit, indem Sie [fflush](fflush.md) verwenden, bevor Sie **_setmode** verwenden, um den Modus zu ändern. Wenn Sie den Code nicht leeren, kann es zu unerwartetem Verhalten kommen. Wenn Sie keine Daten in den Stream geschrieben haben, müssen Sie den Code nicht leeren.

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen hierzu finden Sie unter [globaler Status in der CRT](../global-state.md).

## <a name="requirements"></a>Anforderungen

|-Routine zurückgegebener Wert|Erforderlicher Header|Optionale Header|
|-------------|---------------------|----------------------|
|**_setmode**|\<io.h>|\<fcntl.h>|

Weitere Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example-use-_setmode-to-change-stdin"></a>Beispiel: Verwenden von _setmode zum Ändern von stdin

```C
// crt_setmode.c
// This program uses _setmode to change
// stdin from text mode to binary mode.

#include <stdio.h>
#include <fcntl.h>
#include <io.h>

int main( void )
{
   int result;

   // Set "stdin" to have binary mode:
   result = _setmode( _fileno( stdin ), _O_BINARY );
   if( result == -1 )
      perror( "Cannot set mode" );
   else
      printf( "'stdin' successfully changed to binary mode\n" );
}
```

```Output
'stdin' successfully changed to binary mode
```

## <a name="example-use-_setmode-to-change-stdout"></a>Beispiel: Verwenden von _setmode zum Ändern von "stdout"

```C
// crt_setmodeunicode.c
// This program uses _setmode to change
// stdout to Unicode. Cyrillic and Ideographic
// characters will appear on the console (if
// your console font supports those character sets).

#include <fcntl.h>
#include <io.h>
#include <stdio.h>

int main(void) {
    _setmode(_fileno(stdout), _O_U16TEXT);
    wprintf(L"\x043a\x043e\x0448\x043a\x0430 \x65e5\x672c\x56fd\n");
    return 0;
}
```

## <a name="see-also"></a>Siehe auch

[Dateiverarbeitung](../../c-runtime-library/file-handling.md)<br/>
[_creat, _wcreat](creat-wcreat.md)<br/>
[fopen, _wfopen](fopen-wfopen.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
[_set_fmode](set-fmode.md)<br/>
