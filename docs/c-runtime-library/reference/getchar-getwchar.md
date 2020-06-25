---
title: getchar, getwchar
ms.date: 06/23/2020
api_name:
- getchar
- getwchar
- _o_getchar
- _o_getwchar
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
- getwchar
- GetChar
helpviewer_keywords:
- gettchar function
- characters, reading
- getwchar function
- _gettchar function
- standard input, reading from
ms.assetid: 19fda588-3e33-415c-bb60-dd73c028086a
ms.openlocfilehash: c6a02f16c3ee3d3e3bc4f86026719a1bd2885416
ms.sourcegitcommit: 8645408c7929558b8162f781776d0908d790a41c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/24/2020
ms.locfileid: "85334967"
---
# <a name="getchar-getwchar"></a>getchar, getwchar

Liest ein Zeichen aus der Standardeingabe.

## <a name="syntax"></a>Syntax

```C
int getchar();
wint_t getwchar();
```

## <a name="return-value"></a>Rückgabewert

Gibt das gelesene Zeichen zurück. Diese Funktionen warten auf Eingaben und geben nicht zurück, bis die Eingabe verfügbar ist.

Um einen Lesefehler oder eine dateiendebedingung anzugeben, gibt **GetChar** **EOF**zurück, und **getwchar** gibt **WEOF**zurück. Verwenden Sie für **GetChar** **ferror** oder **feof** , um einen Fehler oder ein Dateiende zu überprüfen.

## <a name="remarks"></a>Hinweise

Jede Routine liest ein einzelnes Zeichen aus **stdin** und erhöht den zugeordneten Dateizeiger, um auf das nächste Zeichen zu zeigen. **GetChar** ist mit [_fgetchar](fgetc-fgetwc.md)identisch, wird jedoch als Funktion und als Makro implementiert.

Diese Funktionen Sperren auch den aufrufenden Thread und sind Thread sicher. Eine nicht sperrende Version finden Sie unter [_getc_nolock _getwc_nolock](getchar-nolock-getwchar-nolock.md).

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen hierzu finden Sie unter [globaler Status in der CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Zuordnung generischer Textroutinen

|TCHAR.H-Routine|_UNICODE und _MBCS nicht definiert.|_MBCS definiert|_UNICODE definiert|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_gettchar**|**GetChar**|**GetChar**|**getwchar**|

## <a name="requirements"></a>Anforderungen

|-Routine zurückgegebener Wert|Erforderlicher Header|
|-------------|---------------------|
|**GetChar**|\<stdio.h>|
|**getwchar**|\<stdio.h> oder \<wchar.h>|

Die-Konsole wird in universelle Windows-Plattform-Apps (UWP) nicht unterstützt. Die Standarddaten Strom Handles, die der Konsole, **stdin**, **stdout**und **stderr**zugeordnet sind, müssen umgeleitet werden, bevor Sie von C-Lauf Zeitfunktionen in UWP-Apps verwendet werden können. Zusätzliche Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Beispiel

```C
// crt_getchar.c
// Use getchar to read a line from stdin.

#include <stdio.h>

int main()
{
    char buffer[81];
    int i, ch;

    for (i = 0; (i < 80) && ((ch = getchar()) != EOF)
                         && (ch != '\n'); i++)
    {
        buffer[i] = (char) ch;
    }

    // Terminate string with a null character
    buffer[i] = '\0';
    printf( "Input was: %s\n", buffer);
}
```

```Output

This textInput was: This text
```

## <a name="see-also"></a>Siehe auch

[Stream-E/A](../../c-runtime-library/stream-i-o.md)<br/>
[getc, getwc](getc-getwc.md)<br/>
[fgetc, fgetwc](fgetc-fgetwc.md)<br/>
[_getch, _getwch](getch-getwch.md)<br/>
[putc, putwc](putc-putwc.md)<br/>
[ungetc, ungetwc](ungetc-ungetwc.md)<br/>
