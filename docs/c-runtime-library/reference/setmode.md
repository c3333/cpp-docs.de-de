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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: 36d2130d4039f1f87f7f54fc26ad02cb8d519b4a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81353834"
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

*Fd*<br/>
Dateideskriptor.

*Modus*<br/>
Neuer Übersetzungsmodus.

## <a name="return-value"></a>Rückgabewert

Im Erfolgsfall wird der vorherige Übersetzungsmodus zurückgegeben.

Wenn ungültige Parameter an die Funktion übergeben werden, wird der Handler für ungültige Parameter aufgerufen, wie in [Parameter Validation (Parameterüberprüfung)](../../c-runtime-library/parameter-validation.md)beschrieben. Wenn die Ausführung fortgesetzt werden darf, gibt diese Funktion -1 zurück und setzt **errno** entweder auf **EBADF**, was einen ungültigen Dateideskriptor angibt, oder **EINVAL**, das ein Argument für den ungültigen *Modus* angibt.

Weitere Informationen zu diesen und anderen Rückgabecodes finden Sie unter [_doserrno, errno, _sys_errlist und _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Bemerkungen

Die **_setmode-Funktion** legt den Übersetzungsmodus der Datei von *fd*in *den Modus* um. Das Übergeben **_O_TEXT** als *Modus* legt den Textmodus fest (d. h. übersetzt). Carriage Return-Line Feed (CR-LF)-Kombinationen werden bei der Eingabe in ein einzeiliges Vorschubzeichen übersetzt. Zeilenvorschubzeichen werden bei der Ausgabe in Kombinationen aus Wagenrücklauf und Zeilenvorschub (CR-LF) übersetzt. Das Übergeben **_O_BINARY** legt den binären (nicht übersetzten) Modus fest, in dem diese Übersetzungen unterdrückt werden.

Sie können auch **_O_U16TEXT**, **_O_U8TEXT**oder **_O_WTEXT** übergeben, um den Unicode-Modus zu aktivieren, wie im zweiten Beispiel weiter unten in diesem Dokument gezeigt.

> [!CAUTION]
> Der Unicode-Modus ist für breit `wprintf`formatierte Funktionen (z. B. ) und wird für schmale Druckfunktionen nicht unterstützt. Die Verwendung einer schmalen Druckfunktion in einem Unicode-Modusstream löst eine Assertion aus.

**_setmode** wird in der Regel verwendet, um den Standard-Übersetzungsmodus von **stdin** und **stdout**zu ändern, aber Sie können ihn für jede Datei verwenden. Wenn Sie **_setmode** auf den Dateideskriptor für einen Stream anwenden, rufen Sie **_setmode** auf, bevor Sie Eingabe- oder Ausgabevorgänge für den Stream ausführen.

> [!CAUTION]
> Wenn Sie Daten in einen Dateistream schreiben, leeren Sie den Code explizit mithilfe von [fflush,](fflush.md) bevor Sie **_setmode** verwenden, um den Modus zu ändern. Wenn Sie den Code nicht leeren, kann es zu unerwartetem Verhalten kommen. Wenn Sie keine Daten in den Stream geschrieben haben, müssen Sie den Code nicht leeren.

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen dazu finden Sie [unter Globaler Status in der CRT](../global-state.md).

## <a name="requirements"></a>Anforderungen

|Routine|Erforderlicher Header|Optionale Header|
|-------------|---------------------|----------------------|
|**_setmode**|\<io.h>|\<fcntl.h >|

Weitere Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Beispiel

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

## <a name="example"></a>Beispiel

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
